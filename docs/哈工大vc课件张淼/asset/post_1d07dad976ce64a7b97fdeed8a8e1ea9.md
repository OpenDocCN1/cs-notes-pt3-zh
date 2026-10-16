
## 作为成员函数重载

□ 双目操作符重载函数的使用格式

```
<类名> a;
<类型> b;
a#b;
或
a.operator#(b);
```

```cpp
class Complex
{
  double real,imag;
  public:
  Complex(){real=0;imag=0;}
  Complex(double r,double i){real=r;imag=i;}
  Complex operator + (const Complex &x) const
  {
    Complex temp;
    temp.real=real+x.real;
    temp.imag=imag+x.imag;
    return temp;
  };
};
```

## 作为成员函数重载

+   □ 单目运算符重载函数的声明格式

```
class <类名>
{
<返回值类型> operator #();
}
```

+   □ 单目运算符重载函数的定义格式

```
<返回值类型> <类名>::operator #(){...}
```

## 作为成员函数重载

+   - 单目操作符重载函数的使用格式

```
<类名> a;
#a;
```

或

```
a.operator#();
```

+   - 对于单目操作符，其重载函数是单目操作符的前置用法。而操作符++和--有前置和后置两种用法。为了能够区分，则可以定义另一个带有int型参数的操作符++和--的重载函数来表示它们的后置用法。

```c
int fun()
{
	static int a=4;
	return a;
}
```

```c
int& fun()
{
	static int a=4;
	return a;
}
```

```
const A fun()
{
	static A a;
	return a;
}
```

```
class A
{
	......
};
```

```
A& fun()
{
	static A a;
	return a;
}
```

```
class Counter
{ int value;
public:
    Counter(){value=0;}
    Counter& operator ++() //前置
    {value++;
    return *this;}
    const Counter operator ++(int) //后置
    { Counter temp=*this;
    ++(*this);
    return temp;}
};
```

## 作为全局（友元）函数重载

+   □ 双目操作符重载函数的定义格式

```
<返回值类型> operator #( <类型1> <参数1>, <类型2> <参数2> )
{ ... }
```

```
class Complex
{double real,imag;
    public:      ......
friend Complex operator + (const Complex &c1,
                        const Complex &c2)
};
Complex operator + (const Complex &c1,
const Complex &c2)
{Complex temp;
temp.real=c1.real+c2.real;
temp.imag=c1.imag+c2.imag;
return temp;};}
```

## 作为全局（友元）函数重载

+   □ 使用格式

```
<类型1> a;
<类型2> b;
a#b
或
operator#(a,b)
```

```
class Complex
{double real,imag;
    public:      ......
friend Complex operator + (const Complex &c1,
                        const Complex &c2)
};
Complex operator + (const Complex &c1,
const Complex &c2)
{Complex temp;
temp.real=c1.real+c2.real;
temp.imag=c1.imag+c2.imag;
return temp;};}
```

## 作为全局（友元）函数重载

+   □ 单目操作符重载函数的定义格式

```
<返回值类型> operator #( <类型> <参数> )
{ ... }
```

## 作为全局（友元）函数重载

□ 单目操作符重载函数的使用格式

```
<类名> a;
#a;
或
operator#(a);
```

## 作为全局（友元）函数重载

+   □ 为了能够区分前置和后置++和--的重载函数，它们的后置用法：

```
<返回值类型> operator++(<类型><参数>,int);
```

## 实例

+   □ 重载操作符+，使其能够实现实数与复数的混合运算。

```cpp
class Complex
{
    double real,imag;

public:

    Complex(){real=0;imag=0;}

    Complex(double r,double i) {real=r;imag=i;}

    friend Complex operator + (const Complex &c1, const Complex &c2)
    friend Complex operator + (const Complex &c, double d)
    friend Complex operator + (double d, const Complex &c)
}
```

```
Complex a(1,2),b(3,4),c1,c2,c3;
c1=a+b;
c2=b+21.5
c3=10.2+a;
```

## 规则和限制

+   - 可以重载 C++ 中除下列运算符外的所有运算符：
+     - `.`
+     - `.*`
+     - `::`
+     - `?:`

+   - 只能重载 C++ 语言中已有的运算符，不可膨胀新的。

+   - 不改变原运算符的优先级和结合性。

+   - 不能改变操作数个数。

## 规则和限制（续）

+   - 经重载的运算符，其操作数中至少应该有一个是自定义类型。
+   - 在重载运算符()、[]、->或者=时，运算符重载函数必须声明为类的一个成员。对于其他的运算符，运算符重载函数可以是成员函数或者友元函数。
+   - 但在某些情况下，操作符必须以全局函数来重载，才能满足使用上的要求。

## 练习

如果在类对象a的类中重载运算符“+”，则 a+3的显示调用（          ）。

+   A. a.operator(3);
+   B. a->operator+(3);
+   C. a.operator+(3);
+   D. 3.operator+(a);

## 赋值运算符的重载

两个同类对象之间可以赋值，其含义是用一个对象的状态来改变另一个对象的状态。

C++编译程序会为每个类定义一个隐式的赋值操作符重载函数，其行为是逐个对成员进行赋值操作。

对象的成员中有动态的数据类型时，就不能直接相互赋值，否则在程序的编译或执行过程中出现编译或运行错误。例如：

```
class Cdemo
{  public:
    CDemo(char *s)
    {  ps = new char[strlen(s) + 1];
        strcpy(ps, s); }
    ~CDemo()

void main()
{  CDemo d1("Key"), d2("Mouse");
    d1 = d2; }
    private:
        char *ps;};
```

```
class CDemo
{public:
    .....
    CDemo& operator = (const CDemo &a)
    {
        if (a.ps) { ps = a.ps;}
        else ps = 0;
        return *this;    }
private:
    char *ps;
};
```

## 赋值运算符的重载

![](img/6d59ef6ebdae7180bd2f8d0def48533b_734_0.png)

栈空间 d1 = d2 堆空间
