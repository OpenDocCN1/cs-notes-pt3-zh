
## `#define`的缺点

• 它只是简单的替换，不进行任何语法检查

## Demo 1: An example of define

```c
#define PI 3.1415;
#define max(A,B) ((A) > (B) ? (A) : (B))
void main()
{
    int i = 4;
    printf("%f\n",PI); /* compile error*/

    max(i++,3);
    /*((i++)>3?(i++):3); */
    printf("%d\n",i);
}
```

## `#define`的替换方法

- const 常量
- 模板内联函数

```cpp
1 const double PI = 3.1415;
2 template<class T>
3 inline const T& max(const T& a, const T& b)
4 { return a > b ? a : b; }
```

## `#include`指令

- 用#include指定文件的内容替换#include所在的的行
- 也是简单的替换，养成在头文件后面加上分号的习惯。
- 用<>或者""括上文件名
  - <>表示在编译器的include目录内查找文件
  - ""表示在当前目录下查找文件
- 文件名中可以带有路径

## 跨平台

```
1 #ifdef linux
2     #include <ext/hash_map>
3     #include <ext/hash_set>
4 #else
5     #include <hash_map>
6     #include <hash_set>
7 #endif
```

## 避免重复包含

![](img/7afade9235e9e9d9b1d009051c946346_452_0.png)

## 使用预编译指令的目的

- 增强程序可读性
- 但是调试时宏可能会带来很多问题
- 精简源代码，提取变化
  - 这一重点更多时使用函数的效果更好，但宏也有其不可替代的优势
- 不编译无用代码，精炼目标代码

## 基本知识之编译器和链接器

- C语言是每个C文件单独编译的
  - 每次只编译一个C文件，看不到其它的C文件
- 编译器
  - 编译器确认每个标识符的类型
  - 我要认识它
- 链接器
  - 链接过程在内存中定位这个标识符
  - 我要唯一地找到它

## 例子3

- a.c文件

```
1 int i=5; /* a.c */
2 foo();
3 main(){
4     printf("%d",foo());
5 }
```

- b.c文件

```
1 int i; /*b.c*/
2 foo(){
3     i*=2;
4 };
```

## 正确例子

- a.c文件
- b.c文件

```
1 int i=5; /* a.c */
2 foo();
3 main(){
4     printf("%d",foo());
5 }
```

```
1 extern int i; /*b.c*/
2 foo(){
3     i*=2;
4 };
```

## a.c文件

```c
#include "b.h" /* * .a .c */
int i=5;
main(){
	printf("%d", foo());
}
```

## b.c文件

```c
#include "b.h" /* * .b .c */
foo (){
	i=2;
};
```

## 不仅正确，而且优雅！

- b.h文件

```
1 #ifndef _B_H /* b.h */
2 #define _B_H
3 foo();
4 extern int i;
5 #endif
```

## 工程-project

工程通常包含：

- 源文件(xxx.c)：一系列相关函数和全局变量的定义
- 头文件(xxx.h)：函数和全局变量的声明，如：函数声明、外部变量声明、宏定义、类型定义...
- 可以将模块编译成.o、.a、.obj或.lib文件，从而保护源代码

使用模块的过程

- 建立一个工程(project)
- 把各模块都加入到工程中
- #include模块的头文件
- 开始使用此模块

## 文件中的变量

- 文件的信息隐藏
  - 用static定义的函数和变量只在此模块（文件）中有效
  - （建议采用）
- 允许被其它文件使用的全局变量
  - 在源文件中定义，不加static修饰
  - 在头文件中进行声明，加extern修饰

```
#include"Area.h"
void main()
{
    double r = 3;
    double area = Circle_Area(r);
    area = Circle_Area(r);
    printf("area of circle is %f\n",area);
    printf("PI is %f\n", PI);
    GetTimes();
    printf("function was called %d times",global_times);
}
```

## 多文件工程实例源码-Area.h

```
#ifndef _AREA_H
#define _AREA_H

extern const double PI;
extern int global_times;
double Circle_Area(double r);
void GetTimes();
#endif
```

## 总结

预处理和模块

预处理

- #define
- #ifndef

模块

- 声明和定义的区别
- 全局变量的定义和声明
- 静态变量的定义

谢谢大家，欢迎提问！

## C语言
第7讲：数组

赵岩

哈尔滨工业大学软件学院

March 6, 2011

## 目录

- 数组的定义，初始化，使用
  - 一维数组
  - 二维数组
- 数组作为函数参数

## 目录

- 数组的定义，初始化，使用
  - 一维数组
  - 二维数组
- 数组作为函数参数
- 字符串数组
  - 字符串定义
  - 字符串输入与输出
  - 字符串处理

## 为什么使用数组-问题

## 问题

要读入某班全体5位同学(语言成绩)，然后进行统计处理(求平均成绩、最高分、最低分……)

## 为什么使用数组

- 用简单变量，需50个不同变量名，要用很多个scanf命令
- 用数组，可共用一个scanf命令，并利用循环结构读取。

```
1 /* without array */
2 int score1,score2,...,score50;
3 scanf("%d,%d,%d",&score1,&score2,&score3);
4 scanf("%d,%d,%d",&score4,&score5,&score6);
5 ........
6 /* use array */
7 int score[50];, /* 优雅 */
8 for (i=0;i<50;i++)
9     scanf("%d",&score[i]);
```

## 数组(array)定义

- 定义
  - 存储属性 数据类型 数组名 [整型常量1] [整型常量2] ... [整型常量n];
  - int a[5];
    - 定义一个有5个元素的数组，每个元素的类型均为int
    - 使用a[0], a[1], a[2], ..., a[4]这样的形式访问每个元素
    - 它和指针变量没有任何区别
    - 系统会在内存分配连续的5个int空间给此数组
    - 数组下标(index)可以是整型表达式
    - 直接访问a的访问，就是访问此数组的首地址

![](img/7afade9235e9e9d9b1d009051c946346_476_0.png)
