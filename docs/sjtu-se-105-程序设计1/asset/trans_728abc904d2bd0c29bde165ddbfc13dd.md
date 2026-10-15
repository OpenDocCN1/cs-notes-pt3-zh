

```cpp
if ( int *pi = getValue() )
{
    pi != 0;  // 这里可以使用*pi
    int result = calc(*pi);

    // ...
}
else
{
    // pi 在这里也可见
    pi == 0
    cout << "error: getValue() failed" << endl;
}
```

## 名字解析

```cpp
void fooBar( int *ia, int sz )
{
    for (int i=0; i<sz; ++i) ... // ok
    for (int i=0; i<sz; ++i) ... // ok: 不同的 i
    for (int i=0; i<sz; ++i) ... // ok: 不同的 i
}
```

## 全局对象和函数

- 一次定义法则
  - 全局对象和非inline 全局函数只有一个定义

- 全局域中的函数声明、对象声明
  - 函数声明指定了该函数的名称以及函数的返回类型和参数表
  - `void f();`
  - 关键字extern 为声明但不定义一个对象提供了一种方法，它承诺了该对象会在其他地方被定义
  - `extern int x;`
  - `extern int x = 0;  //对象定义`

## 全局函数、对象的声明的匹配

- 存在函数、对象声明的差异

- 类型的安全链接
  - 在C++中通过类型安全链接机制，可以把函数参数的类型和数目编码在函数名中。类型安全链接可用来帮助捕捉不同文件中函数声明不匹配的情况，从而为文件之间的函数调用提供了类型检查手段

```
// --- token.C 中 ---
int addToken( unsigned char tok ) { /* ... */ }
```

```
// --- lex.C 中 ---
extern int addToken( char );
```

- 由于类型安全链接，在lex.C 中声明的addToken()将会被标记为未定义的函数，而token.C 中的定义则被视为定义了另外一个函数

## 头文件

- 头文件为所有 extern 对象声明、函数声明以及 inline 函数定义、常量定义提供了一个集中的位置
  - 目的：声明局部化
  - 保证所有文件都包含同一个全局对象或函数的同一份声明
  - 保证了如果需要修改声明，则只需改变头文件的声明

- 头文件也可以在设计阶段规定接口，使得可以清楚地看出，某个程序文件提供了什么服务
  - Java语言中的接口文件(interface)

## 一般头文件内容

- 注释
  - //This file is created on April 1st by Tom
- 预编译指令
  - #include <iostream>
- 全局数据声明
  - extern int n;
  - extern int a[];
- 全局常量定义
  - const float pi=3.14;
- 函数声明
  - void fn();

- 内联函数定义
  - inline void fn(){...};
- 类型声明
  - class A;
- 类型定义
  - enum COLOR{...};
  - class A{...};
- 命名空间定义
  - namespace N{...}
- 模板声明和定义
  - template <class T> class A{...};

## 局部对象

- 自动对象
  - 自动对象所在存储区从声明它的函数被调用时开始，一直直到该函数结束为止。
- 寄存器对象
  - 寄存器对象是一种自动对象它支持对其值的快速存取
- 局部静态对象
  - 局部静态对象的存储区在该程序的整个执行期间一直存在

## 自动对象

- 自动对象所在存储区从声明它的函数被调用时开始，一直直到该函数结束为止
  - 自动对象的存储分配发生在定义它的函数被调用时，分配给自动变量的存储区来自于程序的运行栈
    - 自动对象需要被显式初始化，未经初始化的变量的值可能是任意的
  - 在函数结束时，它的活动记录被从运行栈中弹出，与该自动对象相关联的存储区被真正释放，它包含的任何值都被抛弃
    - 自动对象的地址不应该被作为函数的返回值。
    - 当一个自动变量的地址被存储在一个生命周期长于它的指针时，该指针被称为空悬指针

```
Matrix* trouble( Matrix *pm ){
    Matrix res;
    ...
    return &res;      //error
}
int main()
{
    Matrix m1;
    // ...
    Matrix* mainResult = trouble( &m1 ); //悬空指针
    // ...
}
```

## 寄存器对象

- 寄存器对象是一种自动对象，它支持对其值的快速存取。
  - 如果变量被频繁使用，则寄存器变量可以提高程序的运行速度
  - 关键字register 对编译器来说只是一个建议

```
for ( register int ix = 0; ix < sz; ++ix )
    // ...

for (register int *p = array ; p < arraySize; ++p )
    // ...

bool find( register int *pm, int val ) {
    while ( *pm )
        if ( *pm++ == val ) return true;
    return false;
}
```

## 静态局部对象

- 静态局部对象的存储区在该程序的整个执行期间一直存在，但其可见性在局部域内
  - 与全局变量类似，静态局部变量会被程序自动初始化

## 静态局部对象

```
#include <iostream>
int traceGcd( int v1, int v2 )
{
    static int depth = 1;
    cout << "depth #" << depth++ << endl;
    if ( v2 == 0 ) {
        depth = 1;
        return v1;
    }
    return traceGcd( v2, v1%v2 );
}
```

假设 v1 = 15, v2 = 123

| Times | depth | depth' | v1 | v2 |
|---|---|---|---|---|
| 1 | 1 | 2 | 15 | 123 |
| 2 | 2 | 3 | 123 | 15 |
| 3 | 3 | 4 | 15 | 3 |
| 4 | 4 | 5 | 3 | 0 |

## 名字空间

- 考虑下面代码中来自Jack 和Jill头文件中的参数类型
- class Glob {/*...*/};      // in Jack"s header file jack.h
- class Widget {/*...*/};      // also in jack.h
  
- class Blob {/*...*/};      // in Jill"s header file jill.h
- class Widget {/*...*/};      // also in jill.h
  
- #include "jack.h";      // this is in your code
- #include "jill.h";      // so is this
- void my_func(Widget p)      // oops! – error: multiple definitions of Widget
- {
-     // ...
- }

## 名字空间

- 名字空间是一个具名作用域
- :: 语法用来指定你使用的是哪个名字空间，以及你引用的是具有相同名字对象的哪一个
- 例如, cout 在名字空间std中，你可以写:
- std::cout << "Please enter stuff... \n";

