# # 成员函数的实现和类定义 一起放在头文件中

```
文件名Student.h
class Student{
public:
void p(void);
float score;
protected:
char name;
int age;
};
void Student::p(){
cout<<age
}//直接放在了h文件中
```

C++的名称有

外部链接: 函数定义, 可以在其余文件中使用。不能重复定义。

内部链接: 只能在自己的程序中使用, 可以跨文件重复定义。如: 类型定义、

全局变量、inline函数、模板定义等。

```
文件名aa.cpp
#include "student.h"
void main()
{ void f();
Student a;
a.score=80;
cout<<a.score;
a.p();
f();
}
```

```
文件名bb.cpp
#include "student.h "
void f()
{
Student a;
a.score=90;
a.p();
}
//提示void Student::p()被重复定义
```