# Indrotuction

Linux sed命令是利用腳本進行文件處理。
主要用來簡化對文件的反覆操作、編寫轉換。

# Usage

    sed [-hnV][-e<script>][-f<script文件>][文本文件]

## 參數

    -e 以指定的script來處理文本文件
    -f 以指定的script file來處理文本文件
    -h --help
    -n --quiet --silent 只顯示處理後的結果，不改變文件
    -V --version

## 動作

    a: 新增
    c: 取代
    d: 刪除
    i: 插入
    p: 印出
    s: 取代
    g: global replace. If you removed the /g only first occurrence is changed.

# Example

Find word1 and replace with word2 using sed:

    sed -i 's/word1/word2/g' input


With cat:

    cat testfile | sed 's/word1/word2/g'

Too many //: Change the delimiter to something else, like +

    sed 's+http://+https://www.cyberciti.biz+g' input.txt

# Web

[Linux sed 命令](https://www.runoob.com/linux/linux-comm-sed.html)

[How to use sed to find and replace text in files in Linux / Unix shell](https://www.cyberciti.biz/faq/how-to-use-sed-to-find-and-replace-text-in-files-in-linux-unix-shell/)

[使用 sed 工具在 Linux 環境下快速完成「搜尋取代」的任務](https://blog.miniasp.com/post/2010/12/24/Useful-tool-Find-and-Replace-with-sed-command)