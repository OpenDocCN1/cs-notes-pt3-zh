```
class B{...};
class C{...};
class D{...}:public B, public A{...}
class E{...}:public C{...}
class F{...}:public D, public E{...}
```

（1）构造函数的调用次序？

（2）F(派生类)的内存对象布局为？

![](bbox=[0.143, 0.267, 0.359, 0.373])

# 注意：例中构造函数和析构函数的执行顺序

+   - 多继承的构造函数的调用顺序与单继承的相同，也是遵从先祖先（基类），后自己（派生类）的原则。在多个基类之间则严格按照派生定义时从左到右的顺序来排列先后。而析构函数的调用顺序则与构造函数的正好相反。

# 3．虚基类

现在我们来看一种特殊情况，请观察下面的代码：

```
#include <iostream.h>
#include <iomanip.h>
class A
{
protected:
    int a;
};
class B : public A
{
public:
    void SetA(int i)
    {
        a=i;
    }
    int GetA()
    {
        return a;
```