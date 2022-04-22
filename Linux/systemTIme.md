# Introduction

介紹各種在 Linux 中以手動來調整系統時間的方法，包含 :

* date
* hwclock 
* timedatectl 

一般 Linux 系統的時間都會直接設定以 ntp 網路校時的方式自動調整。

# date

## disolay 

    date
    # 四 11月 17 08:49:21 CST 2016

    date +%Y/%m/%d
    # 2016/11/17

    date +%T
    # 09:12:46

## setting

    sudo date -s "2016/11/11 10:21:32"
    sudo date -s "2016-11-11 10:21:32"
    sudo date -s "20161111 10:21:32"

# hwclock

    #查詢硬體時鐘（RTC）的時間
    sudo hwclock

    # 寫入硬體時鐘
    sudo hwclock -w

# timedatectl

    # 檢視系統時間資訊
    timedatectl

    # 設定系統時間
    sudo timedatectl set-time "2016-11-12 18:10:40"

    # 設定時區
    timedatectl set-timezone "Asia/Taipei"
    # 選單選取
    sudo dpkg-reconfigure tzdata

# Note

如果系統有設定以 ntp 自動校時，在手動更改日期與時間時，就出現這樣的錯誤訊息：

    Failed to set time: Automatic time synchronization is enabled.


    # ntp 關閉
    sudo timedatectl set-ntp no
    
    #ntp 自動校時
    sudo timedatectl set-ntp yes
