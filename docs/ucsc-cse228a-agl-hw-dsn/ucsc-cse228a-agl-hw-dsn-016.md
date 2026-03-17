# 016：变量与数据类型 📚

在本节课中，我们将要学习Python编程中最基础也是最重要的两个概念：**变量**和**数据类型**。理解它们是如何工作的，是编写任何Python程序的第一步。

## 什么是变量？ 🤔

上一节我们介绍了课程概述，本节中我们来看看什么是变量。

变量可以理解为一个**存储数据的盒子**。你给这个盒子起一个名字（变量名），然后把数据（值）放进去。之后，你就可以通过这个名字来使用盒子里的数据。

在Python中，创建一个变量并赋值非常简单，只需要使用等号 `=`。

```python
# 创建一个名为 message 的变量，并将字符串 "Hello, World!" 存储在其中
message = "Hello, World!"
```

现在，变量 `message` 就代表了 `"Hello, World!"` 这个值。当你打印 `message` 时，计算机会输出它存储的内容。

```python
print(message)  # 输出：Hello, World!
```

变量的值是可以改变的，这也是它被称为“变”量的原因。

```python
message = "Hello, Python!"  # 将 message 的值改为新的字符串
print(message)  # 输出：Hello, Python!
```

## 基本数据类型 🔢

变量可以存储不同类型的数据。Python有一些内置的基本数据类型，最常见的有以下几种：

以下是几种核心的数据类型及其示例：

*   **整数 (int)**： 表示没有小数部分的数字，可以是正数或负数。
    ```python
    age = 25
    temperature = -10
    ```
*   **浮点数 (float)**： 表示带有小数点的数字。
    ```python
    price = 19.99
    pi = 3.14159
    ```
*   **字符串 (str)**： 表示文本信息，需要用单引号 `' '` 或双引号 `" "` 括起来。
    ```python
    name = "Alice"
    greeting = 'Hello there!'
    ```
*   **布尔值 (bool)**： 表示逻辑值，只有两种可能：`True`（真）或 `False`（假）。注意首字母大写。
    ```python
    is_student = True
    has_passed = False
    ```

你可以使用 `type()` 函数来查看任何变量或值的数据类型。

```python
print(type(age))        # 输出：<class 'int'>
print(type(price))      # 输出：<class 'float'>
print(type(name))       # 输出：<class 'str'>
print(type(is_student)) # 输出：<class 'bool'>
```

## 变量的命名规则 📝

为了写出清晰易懂的代码，给变量起一个好名字非常重要。Python有一些必须遵守的规则和推荐的惯例：

以下是命名变量时需要遵循的规则：

1.  **只能包含**字母、数字和下划线 `_`。
2.  **不能以数字开头**。例如 `2nd_place` 是无效的，但 `second_place` 是有效的。
3.  **不能使用Python的关键字**（如 `if`, `for`, `while`, `print` 等）作为变量名。
4.  名称是**区分大小写**的。`myVariable`、`myvariable` 和 `MYVARIABLE` 是三个不同的变量。

除了规则，还有一些让代码更易读的**惯例**（良好实践）：

*   使用描述性的名称，比如用 `user_age` 而不是 `a`。
*   对于多个单词组成的变量名，通常使用**蛇形命名法**：用小写字母，单词之间用下划线连接。例如：`first_name`, `total_amount`。

## 简单的操作与类型转换 ⚙️

变量和不同类型的数据可以进行操作。例如，数字可以参与数学运算。

```python
x = 10
y = 3
print(x + y)  # 加法，输出：13
print(x - y)  # 减法，输出：7
print(x * y)  # 乘法，输出：30
print(x / y)  # 除法，输出：3.333...
```

有时，我们需要在不同数据类型之间进行转换。这可以通过一些内置函数实现：

*   `int()`： 将数据转换为整数。
*   `float()`： 将数据转换为浮点数。
*   `str()`： 将数据转换为字符串。

```python
num_str = "100"
num_int = int(num_str)  # 将字符串 "100" 转换为整数 100
print(num_int + 50)     # 输出：150

# 尝试将包含小数的字符串转为整数会报错
# int(“99.9”)  # 这会引发 ValueError

# 正确的做法是先转为浮点数，再转为整数
num_float = float("99.9")
print(int(num_float))   # 输出：99 (直接截断小数部分)
```

## 总结 🎯

本节课中我们一起学习了Python编程的基石：
1.  **变量**是存储数据的命名容器，通过 `=` 赋值。
2.  **基本数据类型**包括整数(`int`)、浮点数(`float`)、字符串(`str`)和布尔值(`bool`)。
3.  变量命名需遵守特定规则，并推荐使用描述性的蛇形命名法。
4.  可以使用 `type()` 函数检查类型，以及 `int()`, `float()`, `str()` 等函数进行类型转换。

理解并熟练运用这些概念，将为后续学习更复杂的Python知识打下坚实的基础。