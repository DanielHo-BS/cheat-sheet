# Introdution

類別(Class)及物件(Object):

* 類別(Class)
* 物件(Object)
* 屬性(Attribute)
* 建構式(Constructor)
* 方法(Method)

# Exmpale

    # 汽車類別
    class Cars:
        # 建構式
        def __init__(self, color, seat):
            self.color = color  # 顏色屬性
            self.seat = seat  # 座位屬性

        # 方法(Method)
        def drive(self):
            print(f"My car is {self.color} and {self.seat} seats.")

## Class

就是物件(Object)的藍圖(blueprint)。類別(Class)就類似設計圖，會定義未來產生物件(Object)時所擁有的屬性(Attribute)及方法(Method)。

    class classname
        statement

## Object

透過類別(Class)實際建立的實體。  
類別(Class)與物件(Object)的關係就像汽車設計圖與汽車實體。

    object_name = classname()

## Attribute

負責存放物件(Object)的資料。

    object_name.attribute_name = value

## Constructor

於建立物件(Object)的同時，會自動執行的方法(Method)。  
通常我們會在建構式(Constructor)中初始化物件(Object)的屬性值(Attribute)。至少要有一個self參數，之後利用逗號區隔其他屬性。


    def __init__(self, color, seat):
    　　self.color = color  # 顏色屬性
    　　self.seat = seat  # 座位屬性 

## Method

可以想像是物件(Object)的行為。方法(Method)和建構式(Constructor)一樣至少要有一個self參數。

    def method_name(self):
    　　statement

# Reference

[Python物件導向-淺談Python類別-Class](https://www.learncodewithmike.com/2020/01/python-class.html)

[Python物件導向-3個必須瞭解的Python屬性觀念](https://www.learncodewithmike.com/2020/01/python-attribute.html)

[Python3 教學 #05 (Ch9: Class: 繼承、建構子、多型、封裝、覆載](https://www.brilliantcode.net/761/python-3-6-class/)