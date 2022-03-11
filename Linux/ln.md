# Introduction

ln (link files) 一个非常重要命令，它的功能是為某個文件在另外的位置建立一個同步連結。當有需要用到相同文件時，就不需要額外建立新的文件，只須建立連結，就可以節省硬碟空間。

## Hard Link

* 以文件副本存在，但實際不站硬體空間
* 不允許建立目錄連結
* 只能在同一個文件系統中才能建立

## Symbolic Link

* 以路徑存在，類似windows系統中的捷徑方式
* 允許跨文件系統
* 可以建立目錄連結
* 可對不存在的文件進行連結

# Usage

     ln [參數][源文件或目錄][目標文件或目錄]

## 參數

### 必要参数：

    -b 刪除，覆蓋以前建立的連結
    -d sudo 建立目錄的hard link
    -f force
    -i 互動模式，文件存在則提醒是否覆蓋
    -n 把連結符號視為一般目錄
    -s symbolic link
    -v vebose

### 選擇參數

    -S "-S<字尾備份字符串>"
    -V "-V<備份方式>"
    --help
    --version

## Example

    ln ../common common



