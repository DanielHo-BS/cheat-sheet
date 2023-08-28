# Change the store path

Here will write some note about how to **change the store path** of ``Docker Desktop``.

## Method

```text
Original Path: C:\Users\<userName>\AppData\Local\Docker
Remove Path: D:\docker\
```

### 1. Turn off ``Docker Desktop``

```text
Docker Desktop > Quit Docker Desktop
```

### 2. Turn off ``WSL`` on **PowerShell**

```bash
wsl --shutdown
```

### 3. Backup the **docker-desktop-data**

```bash
wsl --export docker-desktop-data D:\docker\docker-desktop-data.tar
```

### 4. Unregister docker

```bash
wsl --unregister docker-desktop-data
```

### 5. Import the backup to remove path

```bash
wsl --import docker-desktop-data D:\docker\data D:\docker\docker-desktop-data.tar --version 2
```

### 6. Restart Docker Desktop

After confirming that everything is working properly, proceed to delete the previously backed up docker-desktop-data file (*.tar).

## Reference

[變更 Docker Desktop 儲存位置 (Windows)](https://www.ruyut.com/2022/05/move-docker-desktop-data.html)
