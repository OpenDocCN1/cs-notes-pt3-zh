# 004：Python编程语言入门

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_1.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_3.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_4.png)

在本节课中，我们将学习Python编程语言的基础知识。Python是一门功能强大且易于快速构建应用程序的语言，它内置了许多特性，使得开发过程便捷高效。无论您是否有编程经验，本节课都将带您领略Python的核心功能，包括变量、数据类型、控制流、数据结构、函数、面向对象编程以及一些高级特性。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_6.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_8.png)

## 第一个Python程序

我们从一个简单的“Hello World”程序开始。Python程序通常保存在以`.py`为扩展名的文本文件中。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_10.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_11.png)

```python
print("Hello, world!")
```

要运行这个程序，我们需要在终端中使用Python解释器。Python是一种解释型语言，这意味着解释器会逐行读取并执行我们的代码。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_13.png)

```bash
python hello.py
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_15.png)

运行后，终端会输出“Hello, world!”。我们已经接触到了Python的几个基本概念：解释器、函数（如`print`）和字符串。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_17.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_19.png)

## 变量与数据类型

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_21.png)

与许多编程语言一样，Python也支持变量。变量用于存储数据。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_23.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_25.png)

```python
a = 28
```

Python是动态类型语言，这意味着我们无需显式声明变量的类型。解释器会根据赋给变量的值自动推断其类型。Python中常见的数据类型包括：

*   **整数 (`int`)**: 如 `28`
*   **浮点数 (`float`)**: 如 `1.5`
*   **字符串 (`str`)**: 如 `"hello"` 或 `'hello'`
*   **布尔值 (`bool`)**: `True` 或 `False`
*   **空值 (`NoneType`)**: `None`，表示没有值

## 获取用户输入与字符串操作

我们可以编写程序与用户交互。例如，一个向用户问好的程序：

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_27.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_28.png)

```python
name = input("Name: ")
print("Hello, " + name)
```

`input`函数用于获取用户输入。我们可以使用加号`+`来连接（拼接）字符串。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_30.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_31.png)

另一种更现代、更高效的方式是使用**格式化字符串（f-string）**：

```python
name = input("Name: ")
print(f"Hello, {name}")
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_33.png)

在字符串前加上字母`f`，并在字符串内部使用花括号`{}`包裹变量名，Python会自动将变量的值插入到字符串中。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_35.png)

## 条件语句

条件语句允许程序根据不同的情况执行不同的代码块。Python使用`if`、`elif`和`else`关键字。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_37.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_39.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_41.png)

```python
n = int(input("Number: "))

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_43.png)

if n > 0:
    print("n is positive")
elif n < 0:
    print("n is negative")
else:
    print("n is zero")
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_45.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_46.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_47.png)

**注意**：`input`函数返回的是字符串类型。如果我们需要进行数值比较，必须使用`int()`或`float()`函数将其转换为数字。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_49.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_51.png)

Python通过**缩进**来定义代码块。同一缩进级别的代码属于同一个逻辑块。

## 序列与数据结构

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_53.png)

Python提供了多种强大的数据结构来存储数据集合。

### 列表

列表(`list`)是一种有序、可变的序列，用于存储一组元素。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_55.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_57.png)

```python
names = ["Harry", "Ron", "Hermione"]
print(names[0]) # 输出: Harry

names.append("Draco") # 添加元素
names.sort() # 排序
print(names)
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_59.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_61.png)

### 元组

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_63.png)

元组(`tuple`)是一种有序、**不可变**的序列，通常用于存储不应被修改的相关数据组。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_65.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_66.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_68.png)

```python
coordinate = (10.0, 20.0)
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_70.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_72.png)

### 集合

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_74.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_76.png)

集合(`set`)是一个**无序**的、元素**唯一**的集合。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_78.png)

```python
s = set()
s.add(1)
s.add(2)
s.add(3)
s.add(3) # 重复添加，集合中仍只有一个3
s.remove(2)
print(f"The set has {len(s)} elements.")
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_80.png)

### 字典

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_82.png)

字典(`dict`)存储**键值对**，允许通过键快速查找对应的值。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_84.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_85.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_87.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_88.png)

```python
houses = {"Harry": "Gryffindor", "Draco": "Slytherin"}
print(houses["Harry"]) # 输出: Gryffindor

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_90.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_91.png)

houses["Hermione"] = "Gryffindor" # 添加新的键值对
```

## 循环

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_93.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_94.png)

循环让我们可以重复执行一段代码。Python的`for`循环可以遍历任何序列。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_96.png)

```python
# 遍历数字范围
for i in range(6):
    print(i)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_98.png)

# 遍历列表
names = ["Harry", "Ron", "Hermione"]
for name in names:
    print(name)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_100.png)

# 遍历字符串（字符序列）
name = "Harry"
for char in name:
    print(char)
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_102.png)

`range(n)`函数生成一个从0到n-1的整数序列。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_104.png)

## 函数

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_106.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_108.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_110.png)

函数是一段可重复使用的代码块。我们可以使用`def`关键字定义自己的函数。

```python
def square(x):
    return x * x

for i in range(10):
    print(f"The square of {i} is {square(i)}")
```

### 模块

我们可以将函数保存在不同的文件中，并通过`import`语句在其他文件中使用它们。

**functions.py**
```python
def square(x):
    return x * x
```

**squares.py**
```python
from functions import square

for i in range(10):
    print(f"The square of {i} is {square(i)}")
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_112.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_114.png)

## 面向对象编程

面向对象编程（OOP）允许我们创建自己的数据类型（类）。类定义了对象的蓝图，包含属性（数据）和方法（函数）。

```python
class Point:
    def __init__(self, x, y): # 初始化方法
        self.x = x
        self.y = y

p = Point(2, 8)
print(p.x) # 输出: 2
print(p.y) # 输出: 8
```

`__init__`是一个特殊方法（构造方法），在创建类的新实例时自动调用。`self`参数代表对象实例本身。

让我们看一个更复杂的例子，模拟航班订座：

```python
class Flight:
    def __init__(self, capacity):
        self.capacity = capacity
        self.passengers = []

    def open_seats(self):
        return self.capacity - len(self.passengers)

    def add_passenger(self, name):
        if not self.open_seats():
            return False
        self.passengers.append(name)
        return True

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_116.png)

flight = Flight(3)
people = ["Harry", "Ron", "Hermione", "Ginny"]
for person in people:
    if flight.add_passenger(person):
        print(f"Added {person} to flight successfully.")
    else:
        print(f"No available seats for {person}.")
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_118.png)

## 装饰器

装饰器(`decorator`)是Python中一个强大的功能，它允许我们修改或增强函数的行为，而不改变其原始代码。装饰器本身是一个函数，它接收一个函数作为参数并返回一个新的函数。

```python
def announce(f):
    def wrapper():
        print("About to run the function...")
        f()
        print("Done with the function.")
    return wrapper

@announce
def hello():
    print("Hello, world!")

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_120.png)

hello()
# 输出:
# About to run the function...
# Hello, world!
# Done with the function.
```

## Lambda表达式

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_122.png)

`lambda`表达式用于创建简单的匿名函数（即没有名字的函数），通常用于需要函数对象作为参数的场合。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_124.png)

```python
people = [
    {"name": "Harry", "house": "Gryffindor"},
    {"name": "Cho", "house": "Ravenclaw"},
    {"name": "Draco", "house": "Slytherin"}
]

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_126.png)

# 使用lambda表达式按姓名排序
people.sort(key=lambda person: person["name"])
print(people)
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_128.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_129.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_131.png)

## 异常处理

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_133.png)

在程序运行中，错误或异常情况可能发生。Python使用`try`和`except`块来捕获并处理异常，使程序能够优雅地应对错误，而不是直接崩溃。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_135.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_137.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_138.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_140.png)

```python
import sys

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_142.png)

try:
    x = int(input("x: "))
    y = int(input("y: "))
except ValueError:
    print("Error: Invalid input.")
    sys.exit(1)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_144.png)

try:
    result = x / y
except ZeroDivisionError:
    print("Error: Cannot divide by 0.")
    sys.exit(1)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_146.png)

print(f"{x} / {y} = {result}")
```

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_148.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_150.png)

## 总结

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_152.png)

本节课我们一起学习了Python编程语言的核心概念。我们从最简单的“Hello World”程序开始，逐步探索了变量、数据类型、条件判断、循环、列表、元组、集合、字典等基本数据结构。我们还学习了如何定义和调用函数，如何通过模块组织代码，以及面向对象编程的基础——类的创建和使用。

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_154.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_155.png)

![](img/42813ff5ff6dd9c25a6250e137ad3fb8_157.png)

此外，我们简要了解了Python的一些高级特性，如装饰器、lambda表达式和异常处理，这些工具能让我们的代码更简洁、健壮和强大。Python的这些特性使其成为Web应用开发的绝佳选择。在接下来的课程中，我们将使用Python来构建能够处理用户请求并返回响应的Web应用程序。