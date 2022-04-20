# Introduction

Daemon 直接翻譯，意思為 “守護程序, 惡魔, 魔鬼, 妖魔”

在系統中，都會依照需求安裝許多服務，但這些服務本身並不會自動啟用，針對啟用服務程序，即稱為 Daemon

因此 Linux Daemon 是指背景執行中的服務程序。

# Parameter

* start
* stop
* restart
* status
  
# Activate

**syslgod**

1. /etc/init.d/
2. service
3. systemctl

# Architecture

* 呼叫 Fork() 並且讓父程序結束
* 改變umask為0
* 建立log
* 呼叫setsid()建立一個新的作業階段
* 改變目前的工作路徑到一個安全的地方，也就是說永遠都會存在的路徑。 例如根目錄就是一個很好的選擇
* 關閉沒有必要的檔案描述詞
* 你這隻 daemon 所要做的事

## Note

另外要寫daemon有一點一定要注意，那就是盡可能使用防禦式的寫法來寫程式碼。因為daemon不像一般的程式，如果當掉了，是很難去追原因的。所以錯誤檢查要做好，並且一定要養成輸出log的習慣。

# Reference

[認識背景執行 DAEMON 與手動建立 SERVICE入門](https://hoohoo.top/blog/8088098/)

[寫 linux daemon 的注意事項](https://jasonblog.github.io/note/fcamel/911.html)

[PEP 3143 – Standard daemon process library](https://peps.python.org/pep-3143/)

[A simple unix/linux daemon in Python](http://web.archive.org/web/20131017130434/http://www.jejik.com/articles/2007/02/a_simple_unix_linux_daemon_in_python/)

[在 Linux 上寫你的 Daemon](https://moiamond.github.io/post/%E5%9C%A8-Linux-%E4%B8%8A%E5%AF%AB%E4%BD%A0%E7%9A%84-Daemon/)