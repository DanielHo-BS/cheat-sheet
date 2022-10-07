# [實驗室 server 使用說明](https://docs.google.com/document/u/0/d/1U1uzZTWjYY8kLMfY31sT_A96p7fq9sE59vgymjXeTIw/mobilebasic)

**使用server前，請先上網登記使用時段!!**

# Installation

## [OpenSSH](https://learn.microsoft.com/zh-tw/windows-server/administration/openssh/openssh_install_firstuse)

用於遠端操控server for windows，如conda與jupyter。

1. 開啟 設定，選取 [應用程式] > 應用程式 & 功能，然後選取 [選用功能]。

2. 掃描清單，查看是否已安裝 OpenSSH。 如果沒有，請在頁面頂端選取 [ 新增功能]，然後：
    * 尋找 **OpenSSH**，然後按一下 [安裝]。

## [FileZilla](https://filezilla-project.org/download.php?type=server)

用於local與server資料傳遞‧

1. 自行前往下載、安裝

# Useage

## SSH 連線 server

1. 開啟**powershell** or **cmd** 
2. cmd line 輸入指令進行連線：

```bash
ssh server<number>@<server ip>
``` 

### Check server devices in cmd line:

```bash
watch nvidia-smi  
```

### Save data in User folder:

```bash
cd .. && cd .. && cd data/2TB/<User folder>/  
cd .. && cd .. && cd data/4TB/<User folder>/  
```

### 進入conda環境

建議使用自己的環境，才不會把環境弄髒‧

```bash
# check env list
conda env list
# create 
conda create --name <evn-name> python=3.8
# activate
conda activate <evn-name>
# deactovate env
deactivate
```
### jupyter lab
Before using jupyter, please activate your **conda evn**!!  

You need to open **two** powershell.

In powershell 1:

```bash 
# port xxxx 
jupyter lab --port="<you want>"  
```

In powershell 2
```bash
# port the same xxxx
ssh -N -f -L <you want>:localhost:<you want> server<number>@<ip>
# then, input the password: msplgodman
```

Clike the http from powershell 1 to start **jupyter lab**.

## SFTP

使用**FileZilla Client**，進行local與server的資料傳遞

    * Server IP
    * 使用者名稱 : server<number>
    * 密碼 : ***********
    * 埠號 : 22

