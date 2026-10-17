只是某个函数被调用，而无论它是虚的还是非虚的。同一个函数的基类版本在通常的函数中被调用（无论否）的唯一的方法是直接地调用这个函数。

**问题：** 通常，析构函数的活动是很正常的。但是，如果我们想通过指向某个对象的基类的指针操纵这个对象（这就是，通过它的一般接口操纵这个对象），会发生什么现象呢  
这在面向对象的程序设计中确实很重要。当我们想delete在栈中已经用new创建的类的对象的指针时，就会出现这个问题。如果这个指针（将要被delete得指针）是指向基类的，编译器只能知道在delete期间调用这个析构函数的基类版本。我们已经知道，虚函数被创建恰恰是为了解决同样的问题。幸好，析构函数可以是虚函数，于是一切问题就迎刃而解了。

下面是例子：（见asd例子）

```
//: C15:Pvdest.cpp
// Pure virtual destructors
// require a function body.
#include <iostream.h>
using namespace std;

class Base {
public:
    virtual ~Base() {
        cout << "~Base()" << endl;
    }
};

class Derived : public Base {
public:
    ~Derived() {
        cout << "~Derived()" << endl;
    }
};
```