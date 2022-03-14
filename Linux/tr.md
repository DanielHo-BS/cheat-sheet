# Introduction

Linux tr命令用於轉換或刪除文件中的字符。

類似於 sed指令的簡化版。

# Usage

    tr [-cdst][--help][--version][第一字符集][第二字符集]
    tr [Option]...[SET1][SET2]

# 參數

    -c 反向操作，SET1不處理，不符合的剩餘部分才進行轉換。
    -d --delete
    -t --truncate-set1 削減SET1指定範圍，使之與SET2長度相等。
    -s --squeeze-repeats 將重複的字符刪減，只留下最後一個。
    --version
    --help

# Example

1. a-z to A-Z

    cat testfile | tr a-z A-Z

or

    cat testfile | tr [:lower:][:upper:]

2. delete '\'

cat testfile | tr -d '\\'

# Web

[Linux tr命令](https://www.runoob.com/linux/linux-comm-tr.html)