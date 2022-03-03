# Introduction

rsync 的角色就像是一般 Linux 的 cp 與 scp 指令，可以將檔案或目錄從來源位置複製到目的位置，不過 rsync 在複製檔案時會比 cp 與 scp 更有效率，並且支援連結檔與設備檔（devices），也可以保留檔案的擁有者、群組與權限設定，rsync 在第一次複製檔案時，會複製完整的檔案內容，而之後再次複製檔案時，就會先以 delta transfer 演算法檢查新舊檔案之間的差異，只傳送有變動的部份，可加快備份速度，尤其是在累進備份大檔案時，效果更明顯。另外 rsync 在使用網路傳送資料時，也支援資料的自動壓縮與解壓縮，這樣可以有效減少耗費的網路頻寬。

# Installation

    sudo apt-get install rsync

# 參數

The most common:
* -v : verbose
* -r : recursive 備份所有子目錄下的目錄與檔案
* -a : 封裝備份模式，遞迴備份所有子目錄下的目錄與檔案，保留連結檔、檔案的擁有者、群組、權限以及時間戳記。
* -z : zip
* -h : 將數字以比較容易閱讀的格式輸出。

[其他參數](https://mga8326.blogspot.com/2018/08/rsync.html)

# 遠端備份

rsync 也可以用於不同台機器之間的遠端備份，這樣的用法就跟 scp 指令很像，不過 rsync 會更有效率：

    rsync -avzh /mypath/myfile.gz pi@192.168.1.12:/mybackup/

# 同步刪除檔案

如果您想要讓 rsync 也同步將不存在於來源端的檔案刪除的話，可以加上 --delete 參數，如果沒有來源檔案只有新增、沒有減少的話，它就跟一般的複製動作相同：
* --delete
