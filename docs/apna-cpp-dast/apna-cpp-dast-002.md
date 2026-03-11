# 002：变量、数据类型与运算符 📚

![](img/6b3cc1a9ec6918dde64b75212ab80f20_1.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_2.png)

在本节课中，我们将学习C++编程的基础核心概念：变量、数据类型和运算符。我们将从编写第一个程序开始，逐步理解数据如何在计算机内存中存储，以及如何使用运算符进行各种计算。

---

## 概述

![](img/6b3cc1a9ec6918dde64b75212ab80f20_4.png)

本节课的目标是掌握C++中变量的声明与使用、理解不同的数据类型（如整数、字符、浮点数、布尔值），并学习如何使用算术、关系和逻辑运算符进行基本操作。我们还将学习如何从用户那里获取输入并输出结果。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_6.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_7.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_8.png)

---

![](img/6b3cc1a9ec6918dde64b75212ab80f20_10.png)

## 编写第一个C++程序 👨‍💻

![](img/6b3cc1a9ec6918dde64b75212ab80f20_12.png)

上一节我们介绍了课程大纲，本节中我们来看看如何编写并运行一个简单的C++程序。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_14.png)

一个基本的C++程序结构包含预处理指令和主函数。

```cpp
#include <iostream>
using namespace std;

![](img/6b3cc1a9ec6918dde64b75212ab80f20_16.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_18.png)

int main() {
    // 你的代码写在这里
    return 0;
}
```

*   `#include <iostream>`：这是一个预处理指令，它告诉编译器包含输入输出流库，这样我们才能使用`cout`和`cin`。
*   `using namespace std;`：这行代码让我们可以直接使用`std`命名空间中的标准库函数，比如`cout`，而无需每次都写`std::cout`。
*   `int main() { ... }`：这是程序的主函数。每个C++程序的执行都从这里开始。
*   `return 0;`：表示主函数成功执行完毕。

让我们写一个打印“Hello World”的程序。

```cpp
#include <iostream>
using namespace std;

![](img/6b3cc1a9ec6918dde64b75212ab80f20_20.png)

int main() {
    cout << "Hello World";
    return 0;
}
```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_22.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_23.png)

*   `cout` 用于向屏幕输出内容。
*   `<<` 是流插入运算符，用于将右侧的内容发送到`cout`。
*   每行语句以分号 `;` 结尾。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_25.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_26.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_28.png)

要输出多行文本，可以使用换行符 `\n`。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_30.png)

```cpp
cout << "Hello World\n";
cout << "from Apna College";
```
或者，将 `\n` 放在字符串内部：
```cpp
cout << "Hello World\nfrom Apna College";
```
`endl` 也可以实现换行：
```cpp
cout << "Hello World" << endl;
cout << "from Apna College";
```

编译并运行程序，你将在屏幕上看到输出。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_32.png)

---

![](img/6b3cc1a9ec6918dde64b75212ab80f20_34.png)

## 变量与内存 🧠

![](img/6b3cc1a9ec6918dde64b75212ab80f20_36.png)

上一节我们学会了输出文本，本节中我们来看看程序如何存储和操作数据。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_38.png)

变量是程序中用于存储数据的基本单元。你可以把变量想象成一个带标签的盒子，里面可以存放一个值。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_40.png)

**声明一个变量的语法是：**
`数据类型 变量名;`
例如：
```cpp
int age; // 声明一个名为age的整数变量
```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_42.png)

**给变量赋值：**
```cpp
age = 25; // 将值25存入age变量
```
声明和赋值也可以一步完成：
```cpp
int age = 25;
char grade = 'A';
float price = 99.99;
bool isSafe = true;
```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_44.png)

当你在代码中写下 `int age = 25;` 时，计算机会在内存（RAM）中分配一小块空间（例如4个字节）来存储这个变量。这块空间被命名为 `age`，其中存储的值是 `25`。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_46.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_47.png)

---

## 数据类型详解 🔢

变量可以存储不同类型的数据，这由**数据类型**决定。C++提供了几种基本（原始）数据类型。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_49.png)

以下是主要的基本数据类型：

![](img/6b3cc1a9ec6918dde64b75212ab80f20_51.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_53.png)

1.  **整型 (`int`)**：用于存储整数（如 -10, 0, 42）。在大多数系统上占用4字节内存。
    ```cpp
    int score = 100;
    int temperature = -5;
    ```

2.  **字符型 (`char`)**：用于存储单个字符（如 ‘a’, ‘B’, ‘$’）。占用1字节内存。字符在内存中实际存储的是其ASCII码值（例如 ‘A’ 对应 65）。
    ```cpp
    char grade = 'A';
    char symbol = '$';
    ```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_55.png)

3.  **浮点型 (`float`)**：用于存储单精度浮点数（小数），如 3.14, 99.99。占用4字节内存。
    ```cpp
    float pi = 3.14;
    float discount = 0.15;
    ```

4.  **双精度浮点型 (`double`)**：用于存储双精度浮点数，精度比`float`更高。占用8字节内存。默认的小数都被视为`double`类型。
    ```cpp
    double precisePi = 3.1415926535;
    double price = 99.99;
    ```

5.  **布尔型 (`bool`)**：只有两个可能的值：`true`（真）或 `false`（假）。在底层，`true`通常用1表示，`false`用0表示。
    ```cpp
    bool isRaining = true;
    bool isLoggedIn = false;
    ```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_57.png)

你可以使用 `sizeof()` 运算符来查看某种数据类型或变量占用的内存大小（字节数）：
```cpp
cout << sizeof(int) << endl; // 通常输出 4
cout << sizeof(grade) << endl; // 输出 1
```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_59.png)

---

## 类型转换 🔄

在编程中，有时需要将一种数据类型的值转换为另一种类型，这称为**类型转换**。

*   **隐式转换**：由编译器自动完成。通常发生在将较小范围类型的值赋给较大范围类型的变量时。
    ```cpp
    int num = 10;
    double decimalNum = num; // 隐式将int转换为double，decimalNum变为10.0
    ```
    将`char`赋给`int`会得到其ASCII码：
    ```cpp
    char ch = 'a';
    int asciiValue = ch; // asciiValue 变为 97
    ```

*   **显式转换（强制转换）**：由程序员手动指定。当从大范围类型转换到小范围类型时，可能会丢失数据。
    ```cpp
    double price = 99.99;
    int approxPrice = (int)price; // 显式将double转换为int，approxPrice变为99（丢失小数部分）
    ```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_61.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_62.png)

---

![](img/6b3cc1a9ec6918dde64b75212ab80f20_64.png)

![](img/6b3cc1a9ec6918dde64b75212ab80f20_65.png)

## 用户输入与输出 🖥️

一个完整的程序通常需要与用户交互：获取输入，进行处理，然后输出结果。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_67.png)

*   **输出**：使用 `cout` 和 `<<`。
*   **输入**：使用 `cin` 和 `>>`。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_69.png)

以下是一个获取用户年龄并输出的示例：

```cpp
#include <iostream>
using namespace std;

int main() {
    int age;
    cout << "Enter your age: ";
    cin >> age; // 程序暂停，等待用户输入一个整数
    cout << "Your age is: " << age << endl;

    double price;
    cout << "Enter the price: ";
    cin >> price;
    cout << "You entered price: " << price << endl;

    return 0;
}
```

---

![](img/6b3cc1a9ec6918dde64b75212ab80f20_71.png)

## 运算符 ⚙️

运算符用于对变量和值执行操作。上一节我们处理了输入输出，本节我们来学习如何用运算符处理数据。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_73.png)

### 1. 算术运算符
用于基本的数学计算。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_75.png)

```cpp
int a = 10, b = 3;
int sum = a + b;      // 加法，结果为13
int difference = a - b; // 减法，结果为7
int product = a * b;   // 乘法，结果为30
int quotient = a / b;  // 除法，结果为3（整数除法舍去小数）
int remainder = a % b; // 取模（求余数），结果为1
```
**注意**：两个整数相除 (`int / int`) 结果仍是整数，小数部分被丢弃。若需要小数结果，至少一个操作数应为浮点类型。
```cpp
int a = 5, b = 2;
double result = (double)a / b; // 将a显式转换为double，result为2.5
```

### 2. 关系运算符
用于比较两个值，返回布尔值 (`true` 或 `false`)。
```cpp
int x = 5, y = 3;
cout << (x > y);   // 大于，输出1 (true)
cout << (x < y);   // 小于，输出0 (false)
cout << (x >= 5);  // 大于等于，输出1
cout << (x <= 4);  // 小于等于，输出0
cout << (x == 5);  // 等于，输出1
cout << (x != 3);  // 不等于，输出1
```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_77.png)

### 3. 逻辑运算符
用于组合多个布尔条件。
*   **逻辑与 (`&&`)**：所有条件都为真时，结果才为真。
*   **逻辑或 (`||`)**：至少一个条件为真时，结果就为真。
*   **逻辑非 (`!`)**：反转布尔值。

```cpp
bool condition1 = (5 > 3); // true
bool condition2 = (2 < 1); // false

cout << (condition1 && condition2); // 逻辑与，输出0 (false)
cout << (condition1 || condition2); // 逻辑或，输出1 (true)
cout << (!condition1);              // 逻辑非，输出0 (false)
```

### 4. 赋值与复合赋值运算符
`=` 是基本的赋值运算符。还有复合赋值运算符，可以简化操作。
```cpp
int a = 10;
a += 5;  // 等价于 a = a + 5; 现在a是15
a -= 3;  // 等价于 a = a - 3; 现在a是12
a *= 2;  // 等价于 a = a * 2; 现在a是24
a /= 4;  // 等价于 a = a / 4; 现在a是6
```

### 5. 自增与自减运算符（一元运算符）
用于将变量的值增加或减少1。
*   **前缀形式 (`++a`, `--a`)**：先增减，再使用值。
*   **后缀形式 (`a++`, `a--`)**：先使用值，再增减。

```cpp
int a = 10;
int b = ++a; // a先增加到11，然后赋值给b。结果：a=11, b=11

int x = 10;
int y = x++; // x的当前值(10)先赋值给y，然后x增加到11。结果：x=11, y=10
```

---

## 综合示例：简单计算器程序 🧮

让我们运用所学知识，编写一个执行两个数字加减乘除的程序。

```cpp
#include <iostream>
using namespace std;

int main() {
    int num1, num2;
    
    cout << "Enter first number: ";
    cin >> num1;
    cout << "Enter second number: ";
    cin >> num2;
    
    cout << "Sum: " << (num1 + num2) << endl;
    cout << "Difference: " << (num1 - num2) << endl;
    cout << "Product: " << (num1 * num2) << endl;
    
    if(num2 != 0) {
        cout << "Quotient (int): " << (num1 / num2) << endl;
        cout << "Remainder: " << (num1 % num2) << endl;
    } else {
        cout << "Division by zero is not allowed." << endl;
    }
    
    return 0;
}
```

![](img/6b3cc1a9ec6918dde64b75212ab80f20_79.png)

---

## 总结

本节课中我们一起学习了C++编程的基石：
1.  **程序结构**：如何编写、编译和运行一个基本的C++程序。
2.  **变量**：作为存储数据的命名容器，在内存中占有空间。
3.  **数据类型**：包括 `int`, `char`, `float`, `double`, `bool`，它们定义了变量可以存储的数据种类和大小。
4.  **类型转换**：隐式与显式转换数据类型的机制。
5.  **输入/输出**：使用 `cin` 从用户获取输入，使用 `cout` 向屏幕输出信息。
6.  **运算符**：
    *   **算术运算符** (`+`, `-`, `*`, `/`, `%`) 用于计算。
    *   **关系运算符** (`>`, `<`, `>=`, `<=`, `==`, `!=`) 用于比较。
    *   **逻辑运算符** (`&&`, `||`, `!`) 用于组合条件。
    *   **自增/自减运算符** (`++`, `--`) 用于快速增减变量值。

![](img/6b3cc1a9ec6918dde64b75212ab80f20_81.png)

**课后作业**：尝试扩展上面的计算器程序，使其能够根据用户输入的操作符（如 ‘+’, ‘-‘）执行相应的运算。

掌握这些概念是学习更复杂数据结构和算法的关键一步。继续练习，保持探索！