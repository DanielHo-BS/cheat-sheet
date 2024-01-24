# Debug

## Introduction

Assertion refers to the program reaching a certain point in time and affirming that it must be in a certain state. Specifically, it means asserting that at that point in time, a certain variable must have a specific value, or a certain object must possess certain characteristic values.

## Usage

### Assert

Check the expression; it will trigger an exception if it is false.

```python
# Example
assert expression

assert expression [, arguments]
```

```python
# Shutdown 
print(__debug__)
assert False
```

### Try & Except

Catch the exception.

```python
try:
    <statements>  # Run other code
except <Exception>:
    <statements>  # If the 'name' exception is raised in the try block
except <Exception>, <data>:
    <statements>  # If the 'name' exception is raised, with additional data
else:
    <statements>  # If no exceptions occur
finally:
    <statements>  # must be executed
```

### Raise

Trigger an exception by yourself.

```python
raise [Exception [, args [, traceback]]]
```

## Reference

[使用 ASSERT](https://openhome.cc/zh-tw/python/exception/assert/)

[Python3 assert](https://www.runoob.com/python3/python3-assert.html)

[Debug與測試好幫手](https://chwang12341.medium.com/%E7%B5%A6%E8%87%AA%E5%B7%B1%E7%9A%84python%E5%B0%8F%E7%AD%86%E8%A8%98-debug%E8%88%87%E6%B8%AC%E8%A9%A6%E5%A5%BD%E5%B9%AB%E6%89%8B-%E5%98%97%E8%A9%A6try-except%E8%88%87%E4%B8%BB%E5%8B%95%E5%BC%95%E7%99%BCraise%E8%88%87assert-%E7%A8%8B%E5%BC%8F%E7%95%B0%E5%B8%B8%E8%99%95%E7%90%86-de0099d32bbe)

[Try and Except](https://docs.python.org/zh-tw/3/tutorial/errors.html)

[Built-in Exceptions](https://docs.python.org/3/library/exceptions.html#bltin-exceptions)
