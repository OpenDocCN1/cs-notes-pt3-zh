

## 类名与其它变量名或函数名相同的情况

类名允许与其它变量名或函数名相同，通过如下方法来正确访问：

+   1) 如果一个非类名隐藏了类名，则类名通过加前缀即可。

```
class Sample
{/.....};
void fun(int Sample)
{
class Sample s; //定义一个对象要加前缀
Sample++;
//...
}
```

+   2) 如果一个类名隐藏了非类名，则用一般作用域规则即可。

```
int s=0;
void func()
{
class s{...};
s a;
::s=3;} // class作用域到此结束
int g=s;
```

在函数中定义的类称为局部类，不多见。
作用域在定义该类的函数内。

局部类的成员函数必须在类定义内部定义。

## （3）生命期（生存期）

指一个对象产生后，存活时间的度量。

在生存期内，对象保持它的状态。

整个程序的生命期：全局（静态）数据

静态生命期：静态局部数据

局部生命期：

动态生命期：由new申请到内存空间之后，该空间实体开始有效，直到delete释放该内存空间。

```
//动态生命周期
#include <iostream.h>
int * fn(){
    int* ap=new int;//ap指向的内存空间开始有效
    return ap;
}
int main()
{
    int* bp=fn();
    *bp=15;
    cout<<*bp<<"\n";
    delete bp;//bp 即ap所指，空间释放。
    return 0;}
```

## 二
名字空间

名字空间的作用是建立一些互相分隔的作用域，把一些全局实体分隔开来，避免产生名字冲突。

```
namespace zhs{
class aa {
public:
void aa1(int a=1){id=a;}
int id;
};
int age;
double score;
}
namespace ls{
class aa {
public:
int age;
};
}
```

```
void main(){
ls::aa a;
zhs::score=90.1;
zhs::aa b;
b.aa1(8);
a.age=5;
zhs::age=6;
cout<<a.age<<b.id<<endl;
}
```

## 名字空间

不同人编写的程序组合时会遇到名字冲突的危险

可以包含：变量&对象；常量；函数定义；
类型（结构）定义；名字空间的定义

不能包含：预处理命令；

可以开放定义；可以 {} 外定义

## 名字空间

```
namespace zhs{
class aa;
}
class zhs:: aa {
public:
void aa1(int a=1){id=a;}
int id;
};
namespace zhs{
int age;//仍然是全局变量，隐藏在指定的名字空间而已
double score;
}
int main()
{
zhs::aa a;zhs::age=4;
zhs::score=90.5; a.id=3;
cout<<a.id<<zhs::score<<zhs::age<<endl;
return 0;}
```

{} 外定义

合并定义

## 名字空间

```
namespace zhs{
class aa {
public:
    void aa1(int a=1){id=a;}
    int id;
};
int age;
double score;
}
namespace ls{
void a(){cout<<"Computer"<<endl;};
}
Int main()
{zhs::score=90.1;
cout<<zhs::score<<endl;
ls::a();
return 0;}
```

包含函数

## 名字空间

```
```cpp
namespace zhs{
class aa {
public:
    void aa1(int a=1){id=a;}
    int id;
};
int age;
double score;
void f(){age=1;score=80.5;}
}
namespace ls{
    void a();
}
void ls::a(){cout<<zhs::age<<endl;}
int main()
{ zhs::f();  ls::a();
    return 0;}
```
```

> 替换为：age如何？

## 名字空间

```
namespace zhs{
class aa {
public:
void aa1(int a=1){id=a;}
int id;
};
int age;
double score;
}
namespace ls{
using zhs::age;
void a();
}
void ls::a(){cout<<age<<endl;}

int main()
{ ls::a(); return 0;}
```

## 名字空间

```
namespace zhs{
class aa {
public:
void aa1(int a=1){id=a;}
int id;
};
int age;
double score;
}
namespace ls{
using namespace zhs;
void a(){age=3; score=80.5; cout<<age<<endl;}
}
int age = 2;
int main()
{ ls::a(); cout<<zhs::age<<::age;
return 0;}
```

## 标准名字空间std

标准c++库的所有标识符都是在一个名为std的名字空间定义的。

```
std::cout<<"ok"<<"\n";
```

```
using namespace std;
```

在std中定义和声明所有标识符都可以作为全局量来使用。

```
using std::cout;  using std::string;
```

经常会用到的std成员的using声明组成一个头文件。

## 在c++中使用包含函数库的头文件的两种方法：

+   （1）用c语言的传统方法。
+   #include <math.h>
+   不必用名字空间

+   （2）用c++的新方法。c++标准要求系统提供的文件不包括后缀.h。

在c语言相应的头文件名之前加了一个字母c

```
#include <cmath>
#include<cstdio>
#include<cstring>
using namespace std;
```

## 名字空间

名字空间是一个作用域；

是人为定义的

类就是一个特殊的命名空间

## 一、基本概念

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_122_0.png)

## 对象的特征

状态：静态属性
由其相关联的属性值的集合表示

行为：对象的操作

标志：对象唯一的描述ID

## 类的特征

类是相同对象集合的抽象与描述

类由封装的相关联的属性和操作表示

类有唯一的标识名

对象是类的实例，一个类可以有多个实例

## 二、面向对象的求解

就是力图从实际问题中抽象出封装了数据和操作的对象，通过定义对象的各种属性来描述他们的特征和功能，通过接口的定义描述他们的地位及与其它对象的关系，最终形成一个广泛联系的可理解、可扩充、可维护、更接近于问题本来面目的动态对象模型系统。

## 三、面向对象软件开发

OOA: 面向对象分析(干什么)

OOD: 面向对象设计 (怎样干)

OOP: 面向对象编程 (实现)

注: 面向对象 object-oriented

## 面向对象的演化

数据结构＋算法 不能得到算法的丰富性

（数据结构＋算法） 吻合实际情况

对象＋对象…＋对象＝程序

定义（数据&操作）一>调用

-   课堂练习 书P288 第一题、第二题
-   作业： 钱能P290 第四题

## 创天中文VC++

+   文件
+   编辑
+   查看
+   插入
+   工程
+   编译
+   工具
+   窗口
+   帮助

+   打开... Ctrl+O
+   打开 工作区
+   保存 工作区
+   保存 Ctrl+S
+   另存为
+   全部保存
+   页码设置...
+   打印 Ctrl+P
+   新的文件 >
+   新的工作区 >
+   退出

编译 [试试] 查找文件 1 查找文件 2 结果 SQL Debugging

