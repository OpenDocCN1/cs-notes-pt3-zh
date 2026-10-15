

## 声明与定义

- 不能对同一事物定义两次
  - 定义是在说明这是什么事物
  - 例如

```cpp
int a;        // definition
int a;        // error: double definition
double sqrt(double d) { ... }        // definition
double sqrt(double d) { ... }        // error: double definition
```

- 可以对同一事物声明两次
  - 声明是在说明事物可以如何使用

```cpp
int a = 7;        // definition (also a declaration)
extern int a;        // declaration
double sqrt(double);        // declaration
double sqrt(double d) { ... }        // definition (also a declaration)
```

```cpp
double sqrt(double d);
```

```cpp
double sqrt(double d);
```

```cpp
extern int x;
```

```cpp
extern int x;
```

```cpp
double sqrt(double d)
{
    // calculate the
    // square root of d
}
```

```cpp
int x = 7;
```

## 为什么既有声明又有定义？

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_244_0.png)

## 声明的类型

- 变量
  - `int a;` // no initializer
  - `double d = 7;` // initializer using the = syntax
  - `vector<int> vi(10);` // initializer using the () syntax
- 常量
  - `const int x = 7;` // initializer using the = syntax
  - `const int x2(9);` // initializer using the () syntax
  - `const int y;` // error: no initializer
- 函数(§ 8.5)
- 名字空间(§ 8.7)
- 类型(类和枚举；第9章)
- Templates (第19章)

## 头文件和预处理器

- 头文件持有函数、类型、常量和其他程序组成部分的声明
- 下面的结构：
  - `#include "../../std_lib_facilities.h"` 是一个“预处理器指令”，它会将声明添加到程序中
  - 典型地，头文件只是一个文本(源代码)文件
- 头文件赋予我们对在自己的代码中需要访问的函数和类型的访问权
  - 通常，我们不需要关心这些函数和类型是如何编写的
  - 实际的函数和类型是在其它源文件中定义的
    - 经常是库的一部分

```cpp
#include "../../std_lib_facilities.h"
```

a.h:

```cpp
// declarations:
int get();
void set(int);
...
```

a.cpp:

```cpp
#include "a.h"
// definitions:
int get(){/* ... */}
void set(int i){/* ... */}
...
```

b.cpp:

```cpp
#include "a.h"
...
set(get());
...
```

- 头文件 (a.h)定义了用户代码和实现代码之间的接口
- 在两个.cpp文件中使用相同的 `#include` 声明可以方便一致性检查

## 源文件-陷阱

![](img/d2d3f908f0e1c0f8ca98d9dfbe006a9f_248_0.png)

```cpp
// a.h
// definitions:
int get(){ /* ... */ }
void set(int i){ /* ... */ }
...
```

```cpp
// b.cpp
#include "a.h"
...
int i = get();
set(i);
...
```

```cpp
// c.cpp
#include "a.h"
...
set(get());
...
```

- 头文件 (a.h) 定义了用户代码和实现代码之间的接口的**实现**
- 在两个 .cpp 文件中使用相同的 `#include` 声明会造成**重复定义**

## 作用域

- 作用域是一个程序文本区域
  - 例如
    - 全局作用域 (在任何语言结构的外部)
    - 类作用域 (在类的内部)
    - 局部作用域 (在 { ... } 之间)
    - 语句作用域 (例如，`for` 语句)
- 在一个作用域中的名字可以在这个作用域中以及嵌套在其中的作用域中被访问
  - 在名字被声明之后（“无法向前看 can't look ahead”规则）
- 作用域可以让“事物”保持局部性
  - 防止我的变量和函数等与你的变量和函数之间互相干扰
  - 记住：真实的程序可能会有成千上万的实体
  - 局部性非常好！
    - 尽量使名字是局部的

## 作用域

- 全局作用域
  - 程序的最外层的名字空间域
- 名字空间域
  - 用户可以自定义名字空间
- 局部作用域
  - 包含在函数定义或者函数块中的程序文本部分
  - 包含在复合语句中的程序文本部分
- 类作用域
  - 包含在类的定义中的程序文本部分

```cpp
const int notFound = - 1;

int binSearch( const vector<int> &vec, int val ) {
    int low = 0;
    int high = vec.size() - 1;

    while ( low <= high ){
        int mid = ( low + high ) / 2;
        if ( val == vec[ mid ] ) return mid;
        if ( val < vec[ mid ] ) high = mid - 1;
        else low = mid + 1;
    }

    return notFound;
}
```

局部域

局部域

全局域

## 名字解析

- 函数、变量名需要先声明再使用
  - 该声明对于名字的使用者来说必须是可见的
- 名字解析
  - 把程序中的一个名字与某一个声明相关联
  - 名字解析过程依赖于该名字是如何被使用的以及使用该名字的域

## 局部域内的名字解析过程

- 首先查找使用该名字的域，如果找到一个声明，则该名字被解析；如果没有找到，则查找包含该域的域。这个过程会一直继续下去，直到找到一个声明或已经查找完整个全局域。
- 如果查找完整个全局域还没有找到该名字的声明，则这个名字的用法将被标记为错误
- 同一个域内的名字不能重复
- 在外围域中的声明被嵌套域中的同名声明所隐藏

```cpp
int low;

int binSearch( const vector<int> &vec, int val ){
    int low = 0;
    ...
    while ( low <= high ){ ... }
    ...
}
```

## 名字解析

```cpp
for ( int index = 0; index < vecSize; ++index )
{
    // index 只在这里可见
    if ( vec[ index ] == someValue )
        break;
}

// 错误：index 在这里不可见
if ( index != vecSize ) // 找到的元素
```

