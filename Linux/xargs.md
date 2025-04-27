# xargs Cheat Sheet

`xargs` (eXtended ARGuments) is a powerful tool to build and execute commands from standard input. It's often used in combination with other commands to process lists of files or arguments efficiently.

---

## Common Usage

### 1. Basic Usage: Pass Input to a Command
Pass a list of items as arguments to a command.
```bash
echo "file1 file2 file3" | xargs rm
```
This runs:
```bash
rm file1 file2 file3
```

---

### 2. Handle Multiple Arguments per Command
Use `-n` to specify how many arguments to pass per command.
```bash
echo "file1 file2 file3 file4" | xargs -n 2 rm
```
This runs:
```bash
rm file1 file2
rm file3 file4
```

---

### 3. Custom Placeholder (-I)
Replace a placeholder (like `{}`) with each argument.
```bash
echo "file1 file2 file3" | xargs -I {} mv {} /new_directory/
```
This runs:
```bash
mv file1 /new_directory/
mv file2 /new_directory/
mv file3 /new_directory/
```

---

### 4. Read Input from a File
Suppose you have a file, `files.txt`, with:
```
file1.txt
file2.txt
file3.txt
```
Remove all these files:
```bash
xargs -a files.txt rm
```
This runs:
```bash
rm file1.txt file2.txt file3.txt
```

---

### 5. Using xargs with find
Process files found by `find`:
```bash
find . -name "*.log" | xargs rm
find . -name "*.txt" | xargs -I {} cp {} /backup/
find . -name "*.txt" | xargs wc -l
find . -name "*.log" -print0 | xargs -0 rm
find . -name "*.txt" | xargs ls -l
find . -name "*.log" | xargs -n 10 rm
```

---

### 6. Handling Special Characters (Spaces, Newlines)
Use `-0` with `xargs` and `-print0` with `find`:
```bash
find . -name "*.txt" -print0 | xargs -0 rm
```

---

### 7. Prompt Before Execution (-p)
Add a prompt before executing each command:
```bash
echo "file1 file2 file3" | xargs -p rm
```
It will ask you to confirm before deleting each file:
```
rm file1? (y/n)
```
You can combine with `-r` to only prompt if there is input:
```bash
echo "file1 file2" | xargs -p -r rm
```

---

### 8. Limit the Number of Commands (-L)
Use `-L` to specify how many lines of input per command:
```bash
echo -e "1\n2\n3\n4" | xargs -L 2 echo
```
Output:
```
1 2
3 4
```

---

### 9. Suppress Errors
To prevent errors and suppress verbose output:
```bash
echo "file1 file2" | xargs -I {} cp {} /backup/ 2>/dev/null
```
Or use `|| true` after commands to suppress errors (useful for commands like `rm` or `cp`).

Example:
```bash
echo "file1 file2" | xargs -I {} sh -c 'rm {} || true'
```
This will try to remove each file, but if a file does not exist, the script will not stop with an error.

---

### 10. Run Commands in Parallel (-P)
Run multiple commands in parallel:
```bash
echo "file1 file2 file3" | xargs -P 3 -n 1 mv {} /new_directory/
```

---

## Parameters

| Parameter         | Description                                                    | Example                                  |
|-------------------|----------------------------------------------------------------|------------------------------------------|
| -n <number>       | Number of arguments per command                                | `xargs -n 2 rm`                          |
| -I {}             | Replace {} with each input item in the command                 | `xargs -I {} cp {} /backup/`             |
| -0                | Use null character as delimiter (for spaces/special chars)     | `find . -print0 | xargs -0 rm`           |
| -p                | Prompt before executing each command                           | `xargs -p rm`                            |
| -L <lines>        | Number of input lines per command                              | `xargs -L 2 echo`                        |
| -t                | Print each command before executing it                         | `xargs -t rm`                            |
| -v                | Verbose mode: show each input item being processed             | `xargs -v echo`                          |
| -a <file>         | Read input from a file                                         | `xargs -a files.txt rm`                  |
| -P <number>       | Execute commands in parallel (number of processes)             | `xargs -P 3 -n 1 mv {} /dir/`            |
| -d <delimiter>    | Use a custom delimiter (instead of whitespace)                 | `xargs -d ',' echo`                      |
| --max-lines <n>   | Limit the number of lines of input per command                 | `xargs --max-lines=2 echo`               |
| --replace         | Replace occurrences of {} with input items (alt to -I {})      | `xargs --replace=XX echo XX`             |

---

## References
- https://www.runoob.com/linux/linux-comm-xargs.html
- https://www.ibm.com/docs/zh-tw/aix/7.3?topic=x-xargs-command
- https://blog.gtwang.org/linux/xargs-command-examples-in-linux-unix/
