# Introduction

建構自己的 Python函式(Function)，能夠讓你的程式碼被重複的使用(Reusable)，並且提高維護性及可讀性。

重要觀念: 

* 函式(Function)結構
* 函式(Function)參數
* 函式(Function) *args、**kwargs運算子
* 函式(Function)種類
* 函式(Function)變數範圍(Scope)

## 函式(Function)結構

Python函式的結構包含了def關鍵字、函式名稱、參數及實作內容。

    def func_name(Parameter):
        Parameter += 1

## 函式(Function)參數

呼叫函式時一定要傳入相對的參數個數資料，否則就會出現例外錯誤

### 關鍵字參數(Keyword Argument):

呼叫函式時，在傳入參數值的前面加上函式所定義的參數名稱:

    student(name="Mike", id="A123")

### 預設值參數(Default Argument)：

在函式定義的參數中，將可以選擇性傳入的參數設定一個預設值，當來源端有傳入該資料時，使用來源端的資料，沒有傳入時，則依照設定的預設值來進行運算。

    def student(name, id, grades=100):
        prinf(name, id , grades)

**PS.特別注意，必要參數(Required Argument)一定要放在預設值參數(Optional Argument)的前面。**

## 函式(Function) *args、**kwargs運算子

傳入大量的參數時，在函式上定義過多的參數名稱會讓程式碼的可讀性降低，這時候就可以使用 * 符號來將傳入參數進行打包。

    def student(*info):
        prinf(info)
    
    # 打包成元組(Tuple)資料型態
    student("Mike", "A123", "100")

    # 打包成字典(Dictionary)資料型態
    student(name = "Mike",
            id = "A123",
            grades = "100")

## 函式(Function)種類

* 有回傳值
* 無回傳值
  
## 函式(Function)變數範圍(Scope)

* 區域變數(Local Variable)
* 全域變數(Global Variable)

**想要透過函式來修改全域變數的值，則可以使用 ``global``**

# Reference

[Python教學-5個必知的Python Function觀念整理](https://www.learncodewithmike.com/2019/12/python-function.html) 