# Linux Cheat Sheets

This directory contains quick references and cheat sheets for common Linux commands, tools, and system administration tasks. Use these to quickly look up usage patterns, options, and best practices.

---

## Linux 根目錄結構說明 (Root Directory Structure)

在 Linux 系統中，根目錄（/）是檔案系統的起點，所有檔案和目錄都位於這個根目錄下。Linux 的目錄結構有其命名原因和設計原則，以下是一些常見的根目錄下的目錄及其命名原因：

| 目錄      | 說明 |
|-----------|-------------------------------------------------------------|
| /bin      | Binary 執行檔：系統啟動所需的基本命令，如 ls, cp, cat 等。|
| /boot     | 系統啟動文件：核心映像檔案、GRUB 等引導程式。|
| /dev      | 裝置檔案：所有硬體和虛擬設備的檔案。|
| /etc      | 配置檔案：系統和應用程式的設定檔。|
| /home     | 使用者主目錄：每個使用者的個人檔案和設定。|
| /lib      | 系統程式庫：運行所需的共享庫檔案。|
| /media    | 可移動媒體：掛載 USB、光碟等。|
| /mnt      | 挂載點：手動掛載臨時檔案系統。|
| /opt      | 可選軟體包：第三方應用程式和軟體包。|
| /proc     | 虛擬檔案系統：系統運行資訊，如記憶體、處理器等。|
| /root     | 超級使用者（root）的主目錄。|
| /sbin     | 系統管理命令：root 用的管理工具。|
| /srv      | 服務資料：系統服務的資料夾。|
| /sys      | 系統資訊：硬體設備及內核資料。|
| /tmp      | 臨時檔案：存放臨時檔案，重啟後會刪除。|
| /usr      | 用戶資料：用戶程式、共享庫、本地安裝應用程式等。|
| /var      | 變動資料：日誌、郵件、臨時資料等。|

---

## File Operations
- [FSYNC](fsync.md): File synchronization and data integrity
- [RSYNC](rsync.md): Fast file transfer and synchronization
- [ln](ln.md): Creating hard and symbolic links
- [chmod](chmod.md): File and directory permissions

## Text Processing
- [echo](echo.md): Print text and variables
- [tr](tr.md): Translate or delete characters
- [sed](sed.md): Stream editor for filtering and transforming text
- [jq](jq.md): Command-line JSON processor
- [xargs](xargs.md): Build and execute command lines from input

## System & Networking
- [tmux](tmux.md): Terminal multiplexer for managing multiple terminal sessions
- [smb](smb.md): Samba file sharing
- [system time](systemTime.md): Managing system date and time
- [CAN bus](can.md): Controller Area Network bus commands
- [ipmitool](ipmitool.md): IPMI management and server control
- [journactl](journactl.md): Query and view systemd logs
- [Crontab](crontab.md): Scheduling tasks with cron

---

Browse each cheat sheet for quick command examples, explanations, and best practices.
