# Introduction

「argparse」，使我們的程式執行時可以攜帶參數。

# Usage

## import argparse

```python
import argparse
```

## argparse.ArgumentParser()

```python
# define
parser = argparse.ArgumentParser()
## (prog='argparse_template.py', description='Tutorial')
```
* prog 指的是「程式的名稱」 
* description 指的是「程式的功能敘述」

## add_argument

```python
parser.add_argument('--text', '-t', default='test123456', type=str, required=False,  help='Text for program')
parser.add_argument('--nums', '-n', default='10', type=int, required=False, help='Text for program')
```

* default:預設值(可略)
* type:變數型態(可略)
* required:預設為True(可略)
* help:變數說明 (可略)

## parser.parse_args()

將這些帶入的參數，導入至一個變數裡面。

```python
args = parser.parse_args()
```

## call args

```python
args.text
args.num
```

## HELP

```bash
python test.py -h
python test.py --help
```

# Reference

[Argparse 教學](https://docs.python.org/zh-tw/3/howto/argparse.html)

[python 利用 argparse 使程式執行時可帶參數](https://www.wongwonggoods.com/python/python-argparse/)