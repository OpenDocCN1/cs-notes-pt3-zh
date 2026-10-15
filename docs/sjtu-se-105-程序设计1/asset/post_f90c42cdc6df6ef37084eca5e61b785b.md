
```cpp
double expression(Token_stream& ts){
    double left = term(ts);
    Token t =ts.get();
    //...
}
```

```cpp
double primary(Token_stream& ts){
    Token t = ts.get();
    switch(t.kind){
    case '(' :
        double d = expression(ts);
        //...
        //...
    }
}
```

```cpp
double term(Token_stream& ts){
    double left = primary(ts);
    Token t = ts.get();
    //...
    case '/' :
        double d = primary(ts);
        //...
    //...
}
```

当函数被调用时，语言实现会设置一块内存空间，用于存放包含所有参数和局部变量副本的数据结构

Call of expression():

|  |
|---|
| ts |
| left |
| t |
| Implementation stuff |

- Implementation Stuff是函数返回到调用者和将值返回给调用者所需的信息
- 上面的数据结构称为函数激活记录
- 从函数的角度看，参数只是一个局部变量而已

## 参数传递

- 参数传递是指用函数调用的实参值来初始化函数参数存储区的过程。
- 程序运行栈
  - 与一个函数相关的存储区被称为**活动记录**，活动记录是在程序运行栈中分配的存储区。该存储区一直保持与该函数相关联，直到函数结束为止。
  - 系统在函数的活动记录中为函数的每个参数都提供了存储区，参数的存储长度由它的类型来决定

Call of expression():

|  |  |
|---|---|
| ts |  |
| left |  |
| t |  |
| Implementation stuff |  |
| ts |  |
| left |  |
| t |  |
| d |  |
| Implementation stuff |  |

Call of term():

Direction of stack growth

## 函数调用实现

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_229_0.png)

## 函数调用实现

|  |  |
|---|---|
| Call of expression(): | ts |
|  | left |
|  | t |
|  | Implementation stuff |
| Call of term(): | ts |
|  | left |
|  | t |
|  | d |
|  | Implementation stuff |
| Call of primary(): | ts |
|  | t |
|  | d |
|  | Implementation stuff |
| Call of expression(): | ts |
|  | left |
|  | t |
|  | Implementation stuff |

Direction of stack growth

## 递归函数

- 直接或间接调用自己的函数被称为递归函数
  - 递归函数必须定义一个停止条件

```cpp
int rgcd( int v1, int v2 )
{
    if ( v2 != 0 )
        return rgcd( v2, v1%v2 );
    return v1;
}
```

- 调用一般函数比简单计算要慢
  ```c
  int min( int v1, int v2 )
  {
      return( v1 < v2 << v1 : v2 );
  }
  ```
- 若一个函数被指定为inline 函数,则它的函数体可能在编译期间，在程序中每个调用点上被内联地展开
  `int minVal2 = min(i, j); ⇒ int minVal2 = i < j << i : j;`
- inline 机制用来优化小的、只有几行的、经常被调用的函数。
- 对同一程序的不同文件，如果使用同一个内联函数，该内联函数必须在不同的文件中被定义，并且定义一致
  - 建议把inline 函数的定义放到头文件中

- 程序设计 I
- *Programming I*

Thank You!

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_233_0.png)

## 程序设计 1

*Programming and Data Structure I*

## 第6课

## 作用域

Episode Six

## Scope

部分翻译自Bjarne Stroustrup的课件

部分来自于《C++ Primer》

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_234_0.png)

## 概览

- 技术细节
- 声明
  - 定义
  - 头文件和预处理器
- 作用域
  - 全局作用域
  - 局部作用域
- 名字空间
  - “Using” 语句

## 技术细节

- 是不可或缺的“祸端”
  - 编程语言是一门外语
  - 在学习一门外语时，我们必须学习其文法和词汇
- 因为：
  - 程序必须准确而完备地编写
    - 计算机是非常傻(尽管它很快)的机器
    - 计算机无法猜测你的实际意图(也不该去猜测)
  - 因此我们必须知道这些规则
    - 了解其中的核心部分 (C++ 标准有 782 页)
- 但是，不要忘了
  - 我们学习的是编程
  - 我们的输出是程序/系统
  - 编程语言只是一个工具而已

## 技术细节

- 不要花时间在不重要的语法和语义问题上，条条大路通罗马
  - 就像英语一样
- 大多数设计和编程概念都是相通的，或者至少被主流的编程语言广泛支持
  - 因此使用 C++ 学到的知识可以用于许多其他的语言
- 技术细节与具体的语言相关
  - 但是这里描述的 C++ 的特性在 C、Java 和 C# 中都有相对应的特性

## 声明

- “声明”将名字引入到作用域中
- “声明”还指定了具名对象的类型
- 有时声明还包含一个初始化器
- 在C++程序中，名字在使用之前必须先声明
- 例如:
  - int a = 7; // an int variable named ‘a’ is declared
  - const double cd = 8.7; // a double-precision floating-point constant
  - double sqrt(double); // a function taking a double argument and // returning a double result
  - vector<Token> v; // a vector variable of Tokens (variable)

## 声明

- 声明经常会通过头文件引入到程序中
  - 头文件就是包含了声明的文件，这些声明可以为程序中的其他部分提供接口

- 这使得抽象成为可能–我们不必为了使用cout而了解其细节诸如

- 只要在代码中添加

  ```cpp
  #include "../../std_lib_facilities.h"
  ```

  在std_lib_facilities.h 文件中的声明就都可用了（包括cout）

## 定义

- 完整指定所声明实体的声明被称为定义
  - 例如
    int a = 7;
    int b; // an int with the default value (0)
    vector<double> v; // an empty vector of doubles
    double sqrt(double) { ... }; // i.e. a function with a body
    struct Point { int x; int y; };
  - 不是定义的声明
    double sqrt(double); // function body missing
    struct Point; // class members specified elsewhere
    extern int a; // extern means “not definition”
    // “extern” is archaic; we will hardly use it
