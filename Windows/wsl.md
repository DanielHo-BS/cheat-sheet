# Introduction
WSL 2 可讓 Linux GUI 應用程式在Windows上感覺原生且自然。

## Installation

### Start using  Windows Linux Subsystem

![image](https://i.imgur.com/YaW2rAY.png)

### Install WSL2

1. Update Windows system

2. Start using Virtualization Technology

    Open `Power Shell` with **Administrator**

    ```power shell
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    ```

3. Reboot

4. Set default version of WSL2

    ```power shell
    wsl --set-default-version 2
    ```

5. Install ``Ubuntu`` from **Microsoft Store**

    ![image](https://i.imgur.com/LhRhx6D.png)

6. Check version of WSL on ``cmd`` or ``power shell``

    ```power shell
    wsl --list --verbose
    ```

## Usage

### 文字編輯器

```bash
    gedit
```
### 檔案管理員

```bash
    nautilus
```
### X11 應用程式

* xclock 時鐘
* xcalc 計算機
* xclipboard 剪貼
* xev 事件測試

### 點陣圖形編輯器

GIMP用於影像操作和影像編輯、自由格式繪圖、不同影像檔案格式之間的轉碼，以及更特殊的工作。

```bash
    gimp
```

## Reference

[在Windows 子系統 Linux 版上執行 Linux GUI 應用程式](https://docs.microsoft.com/zh-tw/windows/wsl/tutorials/gui-apps)

[Windows 10 安裝 WSL1、WSL2(手動安裝)](https://hackmd.io/@Kailyn/BkMi80IeF)