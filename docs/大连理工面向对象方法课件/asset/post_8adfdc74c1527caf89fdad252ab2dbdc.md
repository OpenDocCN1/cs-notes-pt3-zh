

## 1. 类的使用

使用一个类实际上是创建一个此类的对象，之后使用它的公有成员函数来达到对此类对象作用的目的。

例如：

```cpp
class point
{
int x,y;
public:
    void setpoint(int vx,int vy)
    {
    x=vx;
    y=vy;
    }
};
void f1()
{
    point p1;
    p1.setpoint(10,10);
    //调用了类的公有成员函数，用“ . 操作符”，
    //p1.setpoint(10,10) 等价于
    p1.point::setpoint(10,10);
}
```

还可以用定义指向此类对象的指针来使用此类成员。例如：

```cpp
void f2()
{
    point *p2;
    p2 -> setpoint(10,10);
}
```

这样当两个或者多个类具有相同名字的成员时，不会产生二义性。

## 2. 关于 “::” 单目作用域运算符

对于成员函数的定义可以放在类定义体之外——这时应该加上类名及 “ :: ”，例如：

```cpp
int Cstring::get_length() { ... }
```

另外，有时在局部变量和全局变量同名时，还用 “ :: ” 来区分他们。例如：

```cpp
#include <iostream.h>
float vl=1.2;
main()
{
    int vl=7;
    cout<<vl<<'\n'<<::vl;
    return 0;
}
```

结果为
```
vl=7
vl=1.2
```

## 3. 关于内联函数

有些简单的成员函数可以在类定义中定义——叫**内联函数（内部函数）**。内联函数的定义有两种方式：**隐式定义**（如上例类中定义）、**显式定义**（在类的定义体之外，用**inline关键字**）。

例如：

```cpp
inline void point::setpoint(int vx,int vy)
{...}
inline int area(int x)
{return x*x;}
```

当然，在类定义体中应该给出函数的原型说明。

### 注意：

- 1. 一般函数调用都涉及到调用时的时间开销，为了避免函数调用，在定义时，加上inline可以使编译器把产生函数代码的拷贝插入到合适的位置。

- 2. **内联函数优于宏**（解决了预处理器宏的缺陷）
  - （1）编译器会进行正确的类型检查，而预处理程序的宏不支持类型检查；
  - （2）内联函数无副作用，而宏有；
  - （3）内联函数可以用调试程序调试，对于宏则不然；

- 3. 使用内联函数可以缩短执行时间，但是会增加程序的长度。故inline应该常用的小（短）的函数。

举一个例子：

```cpp
#define Area(x) (x)*(x)//预处理命令#define定义预处理程序的宏，
宏名字和替换文本。
Cout<<Area(5);
被扩展成cout<<(5)*(5);
Cout<< Area(2+3);
被扩展成cout<<(2+3)*( 2+3) ;//注意圆括号的重要作用（必需的）。
若写成：#define Area(x) x*x
```

提供的参数仍然为2+3，则宏被扩展为：2+3*2+3，结果为11。

所以，内联函数消除了与宏有关的操作，而且解决了函数调用的开销及函数参数检查的问题，内联函数体中出现的每一个参数都无需圆括号（如上面的例子）。

另外，见《Thinking in C++》P146

# 第二次课继续

# 需要注意的问题

# 一. 举例：关于公有接口与内部实现 (ch2 p35)

这样可以达到接口与实现分离的原则。

（1）将类的声明放在某个头文件中从而构成类的公有接口，任何要使用这个类的用户只需要包含这个头文件就可以了。

（2）将类的成员函数的定义放在某个源文件中，从而构成了类的实现。

例1：

```cpp
#include <iostream.h>
Class Count{
Public:
int x; //is not good like this public
void printf() {cout<<" x="<<x<<'\n' ;}
};
main()
{
Count
counter,*countPtr=&counter,&countRef=counter;
counter.x=7;
counter.print();
counter.x=8;
countRef.print();
countPtr->x=9;
countPtr->print();
}
```

运行结果
```
x=7
x=8
x=9
```

说明：例子中x 的副作用。

### 注意：

- 1、在类的作用域内，类的成员可以被该类的所有成员函数访问到，在类的作用域外需要用（1）对象名、（2）对对象的引用、（3）指向对象的指针来访问类的成员。

- 2、类的定义通常放在某个头文件中，类的成员函数的定义放在基本文件名相同的源代码文件中。用到这些类的每一个文件都用#include指令把这些文件包含进来。

请看实例：\\c第三讲\\Example\\example_2\\example_2.cpp

# 例2：

```cpp
//TIME1.H（p36）
#ifndef TIME1_H
#define TIME1_H
Class Time{
Public:
    Time();
    Void setTime(int,int,int);
    Void printMilitary();
    Void printStandard();
Private:
    Int hour;
    Int minute;
    Int second;
};
#endif
```

```cpp
//TIME1.CPP
//成员函数的定义
#include <iostream.h>
#include “time1.h”
Time::Time(){hour=minute=secondd=0;}
Void Time::setTime(int h, int m,int s)
{
    hour=(h>=0&&h<24)?h:0;
    minute=(m>=0&&m<60)?m:0;
    second=(s>=0&&s<60)?s:0;
}
void Time::printMilitary()
{
    cout <<((hour<=10? ”0 ” : ””)<<hour<< “:”
         <<(minute<10? ”0 ” : ””)<<minute<< “:”
         <<(second<10? ”0 ” : ””)<<second;
}
```

```cpp
}

void Time::printStandard()
{
    cout << ((hour == 0 || hour == 12) ? 12 : hour % 12)
         << ":" << (minute < 10 ? "0" : "") << minute
         << ":" << (second < 10 ? "0" : "") << second
         << " " << (hour < 12 ? "AM" : "PM");
}
```

```cpp
//FIG2_5.CPP
#include <iostream>
#include "time1.h"
main()
{
    Time t;
    cout << "The initial military time is ";
    t.printMilitary();
    cout << "\nThe initial Standard time is ";
    t.printStandard();
    t.setTime(13,27,6);
    cout << "\n\nMilitary time after set Time is ";
    t.printMilitary();
    cout << "\nStandard time after set Time is ";
    t.printStandard();
    t.setTime(99,99,99);
    cout << "\n\nAfter attempting invalid settings:\n"
         << "Military time: ";
    t.printMilitary();
    cout << "\nStandard time: ";
    t.printStandard();
    cout << endl;
    return 0;
}
```

# 输出结果：

The initial military time is 00: 00: 00
The initial standard time is 12: 00: 00AM

