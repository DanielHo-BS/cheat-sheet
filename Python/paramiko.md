# Paramiko Cheat Sheet

Paramiko is a Python library for the SSH2 protocol. It lets you connect to remote machines, execute commands, and transfer files securely over SSH.

---

## Common Usage

### 1. SSH Connection and Run Commands
Connect to a remote server and run a command:
```python
import paramiko

# Create an SSH client
ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())  # Automatically add unknown hosts

# Connect
ssh.connect(hostname="your_server_ip", username="your_username", password="your_password")

# Run a command
stdin, stdout, stderr = ssh.exec_command('ls -l')

# Print the output
print(stdout.read().decode())

# Close connection
ssh.close()
```

---

### 2. SFTP Upload/Download Files
Transfer files to/from a remote server using SFTP:
```python
import paramiko

# Create Transport
transport = paramiko.Transport(("your_server_ip", 22))
transport.connect(username="your_username", password="your_password")

# Create SFTP client
sftp = paramiko.SFTPClient.from_transport(transport)

# Upload a file
sftp.put('local_file.txt', '/remote/path/remote_file.txt')

# Download a file
sftp.get('/remote/path/remote_file.txt', 'local_file_downloaded.txt')

# Close
sftp.close()
transport.close()
```

---

### 3. Using Private Key Instead of Password
Authenticate with a private key file:
```python
import paramiko

private_key = paramiko.RSAKey.from_private_key_file('/path/to/private/key.pem')

ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect(hostname="your_server_ip", username="your_username", pkey=private_key)

stdin, stdout, stderr = ssh.exec_command('whoami')
print(stdout.read().decode())

ssh.close()
```

---

## Checking Command Exit Status

Just checking `stdout`/`stderr` is not enough! Some commands might fail silently, or send messages to stderr but still exit successfully, or vice-versa. Use `.recv_exit_status()` to get the real exit code:

```python
stdin, stdout, stderr = ssh.exec_command('your_command')
exit_code = stdout.channel.recv_exit_status()
print('Exit code:', exit_code)
```

### Common Exit Codes
| Exit Code | Meaning                                 |
|-----------|-----------------------------------------|
| 0         | Success                                 |
| 1         | General error                           |
| 2         | Misuse of shell builtins                |
| 126       | Command invoked cannot execute          |
| 127       | Command not found                       |
| 128       | Invalid argument to exit                |
| 130       | Script terminated by Ctrl+C             |
| 255       | Exit status out of range / SSH error    |

- Each program can define its own exit codes.
- Some tools (like rsync, scp, docker, etc.) have their own special exit codes (see their manuals).

**Example for rsync:**
- 23 = partial transfer due to error
- 24 = some files vanished during transfer

**In short:**
| Exit code group | What it suggests                        |
|-----------------|----------------------------------------|
| 0               | OK, success ✅                          |
| 1–127           | Some failure ⚠️                        |
| >127            | Serious error or signal interruption 💥 |

---

## References
- https://www.paramiko.org/
- https://github.com/paramiko/paramiko