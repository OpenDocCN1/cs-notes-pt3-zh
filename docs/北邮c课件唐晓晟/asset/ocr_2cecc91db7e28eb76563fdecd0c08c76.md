# 标准库中的头文件示例

```
#ifndef __cplusplus
// 如果是 C++ 程序
namespace std {
  extern "C" {
  // 见 9.2.4
#endif
/* ...... */
int printf(const char* ...);
#endif __cplusplus
}
using namespace std;
#endif
```

左边代码每一块具体的
实际内部都是相同的，但
是有相同名字同时需要
为不同语言，以此把 C++
能与其它头文件
<stdio.h> 在起来的样子

# 9.2.3 单一定义规则

在一个程序里，任一个类、枚举和模板等都必须只定义唯一的一次。这种规则需要以一种复杂和精细的方式来描述，被称为“单一定义规则(One-Definition Rule, ODR)

+   - 也就是说，一个类、模板或其内联函数 的两个定义能够被接受为同一个唯一定义的实例，当且仅当
+     - 它们出现在不同的编译单位里
+     - 它拥有一个相同的对照相同
+     - 这些条件的意义在两个编译单位中也完全一样

# 单一定义规则(ODR)示例

```
//file1.h
struct S {int a; char b;};
void f(S*);

//file2.c
struct S {int a; char b;};
void f(S*) { /*...*/ }

// ok
// 两个不同的文件都声明了两次
// 重点是
// 堆指针 file2.c 人们不想要得到 S
// 在不同文件被声明了两次
// 或者认为可以自由地修改它
```

```
//s.h
struct S {int a; char b;};
void f(S*);

//file1.c
#include "s.h"

//file2.c
#include "s.h"
void f(S* p) { /*...*/ }
// 基于 ODR 的设计
```

# 单一定义规则的错误示例

```
//file1.h
struct S {int a; char b;};
//file1.c
struct S {int a; char b;};
// Error 重复定义

//file2.h
struct S2 {int a; char b;};
//file2.c
class Point { /*...*/ };
// Error 成员不匹配

//file1.c
typedef int X;
struct S3 {X a; char b;};
//file2.c
typedef def char X;
struct S3 {X a; char b;};
// Error X 的含义被改变了
```

//s.h
struct S {int a; char b;};
//file1.c
#define Point int
#include "s.h"
//...
//file2.c
#include "s.h"
class Point { /*...*/ };
//...
// 假如上面是正确的
// 可能会导致编译器通过
// #include 包含来同时的含义
// 导致在不同的编译单位中
// 比如，在 s.h 中定义 X Point