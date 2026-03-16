# C语言编程基础：P08：简单输入输出 - 华氏度转摄氏度

在本节课中，我们将学习如何编写一个简单的C语言程序，用于将华氏度温度转换为摄氏度。这个程序将演示C语言中的变量声明、基本算术运算以及使用`scanf`和`printf`进行输入输出的方法。

## 程序目标

我们将编写一个程序，要求用户输入一个华氏度温度值（整数），程序将计算并输出对应的摄氏度温度值（整数）。这个程序是学习C语言输入输出和表达式计算的经典入门示例。

![](img/e086835cc4a94c96ce96fdd6d94c0d73_1.png)

## 代码结构与解释

以下是完整的程序代码，我们将逐部分进行解释。

```c
#include <stdio.h>

int main(void) {
    int fahrenheit;
    int celsius;

    printf("Please enter your Fahrenheit as an integer: ");
    scanf("%d", &fahrenheit);

    celsius = (fahrenheit - 32) / 1.8;

    printf("%d Fahrenheit is %d Celsius.\n", fahrenheit, celsius);

    return 0;
}
```

### 1. 包含头文件与主函数

每个C程序都需要一个`main`函数作为入口点。我们使用`#include <stdio.h>`来引入标准输入输出库，以便使用`printf`和`scanf`函数。

### 2. 变量声明

我们声明了两个整型变量`fahrenheit`和`celsius`，分别用于存储用户输入的华氏度温度和计算得到的摄氏度温度。

### 3. 获取用户输入

程序使用`printf`函数向用户显示提示信息。接着，使用`scanf`函数读取用户输入的整数。`%d`是格式化字符串，表示读取一个整数。`&fahrenheit`中的`&`符号是取地址运算符，它告诉`scanf`将读取的值存入变量`fahrenheit`所在的内存地址中。

### 4. 温度转换计算

温度转换的核心是以下公式：
**celsius = (fahrenheit - 32) / 1.8**
在代码中，我们直接使用这个公式进行计算。需要注意的是，常量`1.8`是一个双精度浮点数，因此整个表达式会以浮点数方式进行计算，结果再被转换为整数赋值给`celsius`变量。

### 5. 输出结果

计算完成后，我们使用`printf`函数输出结果。格式化字符串`"%d Fahrenheit is %d Celsius.\n"`中的两个`%d`会被变量`fahrenheit`和`celsius`的值依次替换。

### 6. 程序结束

`return 0;`语句表示`main`函数正常结束，并向操作系统返回状态码0。

## 运行示例

编译并运行此程序，你将看到类似以下的交互过程：

```
Please enter your Fahrenheit as an integer: 32
32 Fahrenheit is 0 Celsius.
```

```
Please enter your Fahrenheit as an integer: 212
212 Fahrenheit is 100 Celsius.
```

```
Please enter your Fahrenheit as an integer: 92
92 Fahrenheit is 33 Celsius.
```

## 总结

本节课中，我们一起学习并实现了一个华氏度转摄氏度的C语言程序。通过这个简单的例子，我们掌握了以下几个核心概念：
1.  C程序的基本结构（`main`函数）。
2.  如何使用`int`类型声明变量。
3.  如何使用`printf`进行输出和`scanf`进行输入，特别是`&`取地址运算符的用法。
4.  如何编写和执行一个包含算术运算的表达式。
5.  理解程序中可能发生的隐式类型转换。

![](img/e086835cc4a94c96ce96fdd6d94c0d73_3.png)

![](img/e086835cc4a94c96ce96fdd6d94c0d73_5.png)

这个程序是经典教材《C程序设计语言》中早期示例的简化版本，是迈向更复杂C语言编程的坚实一步。