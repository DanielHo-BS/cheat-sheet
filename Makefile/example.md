# Makefile Example

Here show that example of **makefile**.

## Parameter

gcc: 

* -c :編譯但不進行鏈結
* -ansi : 程式要求依據 ansi 標準，增加可移植性。
* -I : 追加 include 檔案的搜尋路徑
* -Wall : 編譯時顯示所有的警告訊息
* -g : 編入除錯資訊 (要使用 GDB 除錯一定要加)。
* -O ：表示最佳化的程度，預設是 -O1，可以指定 -O2 或 -O3，數字越大最佳化程度越高。

## Usage

```makefile
all: hello

# declare variables
CC = g++
INSRDIR = /usr/local/bin
INCLUDE = .
CFLAGS = -g -Wall -ansi
LIBS += -framework CoreFoundation

hello: hello.cpp 2.cpp 3.cpp a.h b.h c.h
    $(CC) -o hello -I$(INSRDIR) $(CFLAGS) -c hello.cpp 2.cpp 3.cpp 

clean:
    rm hello
```