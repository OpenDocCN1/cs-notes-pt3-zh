# Class CCircle;

# 注意：

+   - 不能在末尾加上一对大括号“{}”，因为这样的话，上面的代码就会被当作一个类的定义，一个类可以有**多个声明**，但是它只能有**一个定义**，对于函数也是这样。

上面的代码和类的定义的**差别**在于它没有一对大括号“0”，这样，我们就可以在定义类CCircle定义指向一个类CCircle的**对象的指针**（举例.ppt）和引用。但是，这时CPoint的代码不能像上面那样写，这是因为在成员函数IsInCircle中我们使用了类CCircle中定义的数据成员，而在此之前编译器只知道可以使用一个名为CCircle的类。

但是不知道这个类中包括了什么样的成员，因此上面的代码在**编译时仍然通过**。

如何解决所遇到的新问题呢？回过头来看类CPoint的定义，我们在定义类的同时定义了成员函数IsInCircle，联想到C语言中的函数，我们可以很自然的想到，可不可以先声明成员函数IsInCircle，然后再定义它呢？如果可以这样的话，我们就可以在类CPoint的定义中先声明成员函数IsInCircle，然后在定义了类CCircle之后再添加成员IsInCircle的定义。

事实上我们正是基于这个想法来解决问题的。我们的确可以先在类CPoint的定义中声明成员函数IsInCircle，然后在后面添加它的定义，完整的代码如下。

请看实例：\\b第二讲\\Example\\ch2.cpp

```
```cpp
#include <iostream.h>
class CCircle;//声明
struct CPoint
{
    unsigned x;
    unsigned y;
    bool IsInCircle(CCircle *Circle);//声明
};

class CCircle
{
public:
    unsigned Radius;
    CPoint Center;
};

bool CPoint::IsInCircle(CCircle *Circle)
{
```
```