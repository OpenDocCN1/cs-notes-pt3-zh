

## 名字空间里的运算符示例

```
namespace std{
    class ostream{
        char* p = "Hello";
        ostream& operator<<(const char*);
    };
    extern ostream cout;
    class string{
        // ...
    };
    ostream operator<<(ostream&, const string&);
}
```

## 一元运算符的解析方式

- 考虑一元运算符@，如果x的类型为X而y的类型为Y，x@y将按照如下方式解析
  - 若@类是，查询作为X的成员函数或者Y的某个基类的成员函数的operator@()声明
  - 在函数@()的环境中查询operator@的声明
  - 若在名空间内里定义了@，在全局查询operator@的声明
- 当查询到operator@重载时，按照重载规则处理
- 一元运算符的解析方式与二义类似

## 11.3 一个复数类型

- 我们希望实现一个复数类，可以进行如下操作
- 此外，还希望提供一些运算符，例如一些比较、<<输出等

```
void f()
{
    complex a=complex(1,2);
    complex b=3;
    complex c=a+2.3;
    complex d=2+b;
    complex e=-b-c;
    b=c*2*c;
}
```

## 11.3.1 成员运算符和非成员符

- 作者喜欢让尽量少的函数能直接去操作对象的表示，因此，作者只允许本类去定义那些本质上需要修改第一个参数值的运算符，如十=，而像+这样基于参数的值简单产生新值的运算符，则在类之外利用基本运算符来定义

## 成员运算符和非成员示例

```
class complex {
{
    double re, im;
public:
    complex&
    operator+=(complex a);
};

complex operator+(
    complex a, complex b)
{
    complex r=a;
    return r+=b;
}

complex& complex::operator+=(
    complex a)
{
    re += a.re; im += a.im;
    return *this;
}

void f(complex x, complex y,
        complex z)
{
    complex r1=x+y+z;
    // r1 = operator+
    // (operator+(x,y), z)
    complex r2=x;
    r2+=y;
    // r2+=y;
    r2+=z;
}
```

## 11.3.2 混合模式算术

- 为了处理complex d=2+b，我们需要能够接受不同类型的运算符的运算等，为此，可以简单地增加运算符的版本来解决这个问题

```
class complex {
{
    double re, im;
public:
    complex& operator+=(
        complex a)
    {
        re += a.re; im += a.im;
        return *this;
    }
};

complex operator+=(
    double a);
{
    re += a;
    return *this;
}
```

## 混合模式算术示例

```
complex operator+=(complex a, complex b)
{
    complex r=a;
    return r+=b; // 调用complex::operator+=(complex)
}

complex operator+=(complex a, double b)
{
    complex r=a;
    return r+=b; // 调用complex::operator+=(double)
}

complex operator+=(double a, complex b)
{
    complex r=b;
    return r+=a; // 调用complex::operator+=(double)
}
```

## 11.3.3 初始化

- 我们可以使用标准对象complex变量进行初始化和赋值。为此，可以定义一个具有一个参数的构造函数来解决这个问题

```
class complex {
    double re, im;
public:
    complex(double r) : re(r), im(0) {}
    complex(): re(0), im(0) {}
};

complex b = 3; // b.re = 3, b.im = 0
complex(3)
complex c;
```

## 11.3.4 复制

除了显式的构造函数之外，complex还按照默认规定，得到了一个定义好的复制构造函数。默认的构造函数就是简单地复制成员，这对于complex类来说已经足够好

```
class complex{
    double re, im;
public:
    complex(const complex& c) : re(c.re), im(c.im) {}
};
```

## 11.3.5 构造函数和转换

前面的例子中，我们为每个标准的算术运算定义了三个版本
complex operator+(complex, complex);
complex operator+(complex, double);
complex operator+(double, complex);

若函数中需要处理的每个参数有三种类型，那么一个参数的函数就需要3个版本，两个参数的需要9个版本，三个参数就需要27个版本，而且这些不同版本的函数代码实现将会非常相似

依靠类型转换可以大大简化此类问题

## 构造函数和转换示例

例如：complex类提供了一个构造函数，能够将double转换为complex。因此，我们就只需要为complex的==运算符定义一个版本

```
bool operator==(complex,complex);
void f(complex x, complex y)
{
    x == y; // operator==(x,y)
    x == 3; // operator==(x, complex(3))
    3 == x; // operator==(complex(3), x)
}
```

## 11.3.6 文字量

不能为类制定文字量(例如：double类惯的1.2或者12e3等)

但是，我们常常可以利用内部类型的文字量。只要通过类的成员函数对其提供一种解释

当构造函数很简洁并且被内联时，把这种以文字量为参数的构造函数就看成是文字量也是相当合理的

例如：可以把complex(3)看成是complex类类型的文字量，虽然从技术上说它并不是

## 11.3.7 另一类成员函数

- 为了使得complex更好的工作，还可以定义复数相等函数，比如说：检查实部和虚部的值，然后利用这些函数进行各种有用的运算

```
class complex{
    double re, im;
public:
    double real() const { return re; }
    double imag() const { return im; }
};
inline bool operator==(complex a, complex b)
{
    return a.real()==b.real() && a.imag()==b.imag();
}
```

## 11.3.8 协助函数

- 将所有的东西集中到一起，complex就变成了

```
class complex
{
    double re, im;
public:
    complex(double r=0, double i=0) : re(r), im(i) {}
    double real() const { return re; }
    double imag() const { return im; }
    complex& operator+=(complex);
    complex& operator-=(double);
    // ==, !=, *, / == ...
};
```

## 协助函数

- 除此之外，还必须提供一批协助函数
  - complex operator+(complex, complex);
  - complex operator+(complex, double);
  - complex operator+=(double, complex);
  - // -, *, /, ...
  - complex operator+(complex); // 一元正号
  - complex operator-(complex); // 一元负号
  - bool operator==(complex, complex);
  - bool operator!=(complex, complex);
  - ostream& operator<<(ostream&, complex&);
  - ostream& operator>>(ostream&, complex&);

## 11.4 转换运算符

- 虽然通过构造函数来进行类型转换确实很方便，但是构造函数也无法达到
  - 从用户类型到一个内部类型的转换（因为内部类型不是类）
  - 从类类型到某个已有类型的转换（而不是修改那个已有类的声明）
- 这些问题可以通过为派生类定义转换运算符的方式解决
- 成员函数X::operator T()，其中T是一个类型名，定义了一个从X到T的转换

