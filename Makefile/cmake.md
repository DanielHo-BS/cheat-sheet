# **CMake**

簡單講，C++ 語言本身雖然跨平台。但是編譯 C++ 的工具鏈卻不跨平台。

* Linux: Makefile 
* Windows: Visual Studio 

針對這個問題，可以考慮 CMake 這類跨平台工具。

藉由 CMake ，可以寫一份完全中立、跟平台無關的專案腳本，編譯時轉換成當前平台的工具鏈。

# Usage

建立CMake 專案

目錄底下:

* ``CMakeLists.txt``
* ``main.cpp``

## CMakeLists.txt

### Common

```txt
cmake_minimum_required(VERSION 3.10) # 設定最低版本要求
project(HelloCMake)                  # 專案名稱
add_executable(MyHomework main.cpp)  # 執行檔名叫 MyApp，原始碼 main.cpp
```

### With HeaderFile

```txt
# 最低要求的 cmake 版本
make_minimum_required(VERSION 2.8)
 
# project name
project(main)
 
# flags
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14")
 
# 確認需要連結的 module 存在
find_package(OpenCV REQUIRED)
 
# 輸出的執行檔
add_executable(main main.cpp)
 
# 連結到 libaries
target_link_libraries(main ${OpenCV_LIBS})
```

通常各家都會有CMake範例，這裡就不一一記錄。

## Compiler

```bash
mkdir build
cd build
cmake ..
```

 CMake 的慣例，將產生的檔案和原始專案區分開來，不污染原始專案。一旦該子目錄放進版控忽略清單後 (如 .gitignore)，這些轉換產生的檔案就不會影響版控，相當方便。

### Linux

Using ``MakeFile``

```bash
make
```

# Reference

[CMake：快速上手跨平台 C++ 專案建置](https://chchwy.github.io/posts/2021-08-10-cmake-basics/)

[簡單的 CMake 介紹以及用法](https://yypw.wordpress.com/2020/06/20/%E7%B0%A1%E5%96%AE%E7%9A%84-cmake-%E4%BB%8B%E7%B4%B9%E4%BB%A5%E5%8F%8A%E7%94%A8%E6%B3%95/)