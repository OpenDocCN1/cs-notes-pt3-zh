
## 程序书写结构

```
/*
 * Function: raiseToPower
 * Usage: int p = raiseToPower(n, k);
 * -----------------------------
 * Returns the integer n raised to the kth power.
 */
int raiseToPower(int n, int k) {
    int result = 1;
    for (int i = 0; i < k; i++) {
        result *= n;
    }
    return result;
}
```

Function comment

Function definition

## 程序开发的步骤

- 程序开发步骤是什么？

1. 编辑（写程序）→
2. 编译（将单独的程序文件变成目标代码）→
3. 链接（将多个编译好的目标代码整合成可执行程序）→
4. 调试执行（查找程序中的错误并运行）

## Java

脚本语言

JavaScript、VBScript

## 程序开发的步骤

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_59_0.png)

source file

object file

executable file

library file

compiler

linker

```
File: HelloWorld.cpp
// This file is adapted from the example
// code of "Programming and Problem Solving with C++"
// Book "C++ Programming Language"

using namespace std;
#include <iostream>

int main() {
  cout << "Hello, world!" << endl;
  return 0;
}
```

## 编程操作流程

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_60_0.png)

## 程序编辑

- 源程序
  - 程序员编辑的程序，存放在*.cpp文件中
  - .h文件是头文件，用来提供函数声明、常量定义、全局数据声明等等
    - #include 指示符读入指定文件的内容，头文件通过include 预处理器指示符而成为我们程序的一部分。
      - `#include <some_file.h>`
      - `#include "my_file.h"`
  - 预处理器指示符用#号标识，这个符号将放在程序中该行的最起始一列上。处理这些指示符的程序被叫做预处理器
    - `#include, #ifdef, #define`

## 程序编辑

- Example: 头文件与#include
  - a.h
  - a.cpp

```
/*A header file*/
```

```
#include "a.h"
int main() { return 0; }
```

→

```
/*A header file*/
int main(){ return 0; }
```

## 程序编译

- 预处理
- 编译
  - 程序被编译后，会生成目标代码，存放在目标文件*.obj中。
  - 目标代码即机器代码，是计算机能够识别的指令集合。

## 程序链接

- 目标代码不能在计算机上运行
  - 目标代码只是个独立的程序段，程序段之间还没有彼此呼应，程序段中用到的C++库代码和其他资源还没挂上
- 为了将成组的目标代码转换为可执行程序，必须进行链接，即将目标代码整合成可执行文件*.exe

- 调试(Debug)
  - 搜索并消除程序中的错误

- 程序员执行目标代码，检查输出结果是否与预期结果一致，从而可以发现程序中的错误。

- 传统定义
  - 确切地告诉 “一个运行速度极快的白痴” 它应该做些什么
  - 在计算机上解决问题的计划
  - 指定程序执行的顺序
    - 但是现代程序通常包含上百万条代码
    - 并且以数据操作为中心

- 我们使用的定义
  - 指定程序的结构和行为，并测试该程序是否能够正确地执行其任务，并具有可接受的性能
    - 时刻牢记要检查 “它” 能否正常工作

- 软件 == 一个或多个程序

- 编程相当简单
  - 只是声明机器该做些什么
- 那么为什么编程又那么难呢？
  - 我们想让 “机器” 做更复杂的事情
    - 计算机又是非常挑剔、无情和愚蠢的东西
  - 世界远比我们想象的要复杂
    - 因此我们不能总是知道我们想要的意味着什么
  - “编程需要领悟”
    - 当你对某个任务编程时，你首先需要理解它
    - 当你编程时，你需要花大量的时间去理解想要自动化执行的任务
  - 编程需要理论联系实践
    - 如果只是实践，那就会产生不可扩展和不可维护的程序
    - 如果只是理论，那就只能编写出过家家一样的程序

## 总结

- 软件概念
- 问题解决策略
- 低级、高级程序设计语言
- 程序
- 过程化程序设计方法
- 对象化程序设计方法
- C++地位与角色
- Hello World程序
- 程序开发步骤

## 程序设计1

# *Programming I*

## 第2课
对象、类型和值

## Episode Two

## Objects, Types, and Values

翻译自Bjarne Stroustrup的课件

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_71_0.png)

- 大多数编程任务都涉及对数据的操作，本章将
  - 描述如何输入输出数据
  - 介绍持有(存储)数据的变量这个概念
  - 介绍核心概念：类型 和 类型安全

- 字符串与字符串I/O

- 整数与整数I/O

- 类型与对象

- 类型安全

## 输入和输出

- 真正的程序需要获得输入，并产生相应的输出
- 计算机内存中放置输入值的空间被称为对象(Object)
  - 对象是内存中的一块区域，它具有某种类型(type)
  - 类型指定了在该区域中可以放置何种信息
- 具名的对象被称为变量(variable)
  - string变量和int变量
  - 变量中存储的数据项称为值(value)

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_73_0.png)

## 输入和输出

```cpp
// 读入 first name:
#include "std_lib_facilities.h"        // 课程头文件

int main()
{
    cout << "Please enter your first name (followed " << "by 'enter'):\n";
    string first_name;
    cin >> first_name;
    cout << "Hello, " << first_name << "\n ";
}
```

// 注意：一行语句可以输出多个值  
// 引入变量的语句称为声明(declaration)  
// 变量持有指定类型的值  
// 最后的 return 0; 在 main() 中是可选的  
// 但是最好加上它以避免编译器报错

std_lib_facilities.h:

Interfaces to libraries
(declarations)

Myfile.cpp:

```
#include "std_lib_facilities.h"

My code
My data
(definitions)
```

- "std_lib_facilities.h" 是课程中用到的头文件

## 变量

- 计算机内存中放置输入值的空间被称为对象(Object)
  - 具名的对象被称为变量(variable)
  - 变量具有某种类型(type)
  - 变量中存储的数据项称为值(value)

定义变量的语句被称为变量定义(definition)

- 定义变量时将在内存中分配一块空间给标量
- 定义变量时可以给变量赋初值（这往往是个好习惯）

```
string name = "Annemarie ";
int number_of_steps = 39;
```

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_76_0.png)

```
string name2 = 39; // error: 39 isn't a string
int numbe_of_steps = "Annemarie "; // error: "Anne marie" is not an int
```
