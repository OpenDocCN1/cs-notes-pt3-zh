
## 思考

## const常量、引用的初始化问题？

```
class A
{
int x;
const int y=1; //error
int &z=x; //error
public:
A()
{
x=0;
y=1;// error, y是常量成员，其值不能改变
}
};
```

```
```cpp
class A {
	int x;
	const int y;
	int &z;

public:
	A():z(x),y(1),x(0)
	{
	}
};
```
```

## 成员初始化表（在定义构造函数时）

成员初始化表中成员初始化的书写顺序并不决定它们的初始化顺序，数据成员的初始化顺序由它们在类定义中的说明顺序来决定。

当类中有常量数据成员或引用数据成员时，如果类中定义了构造函数，则一定要在定义的所有构造函数的成员初始化表中对它们进行初始化，如果类中没有定义构造函数，则编译程序不会给该类生成一个默认构造函数。因此，这样的类程序是不能用于创建对象的。

## 思考

程序运行的某个时刻，一个对象的所有数据成员的值反映了这个对象在该时刻的状态。在不同时刻，对象的状态可能是不同的，对象状态的改变往往是由于对象处理了一条消息（某个成员函数被调用）。但是并不是每条消息都会导致对象状态的变化。有些消息只是获取对象在某时刻的状态。

## 第四章 类与对象

- 类
- 对象
- 构造函数和析构函数
- *const*成员函数
- 成员对象
- 静态成员
- 友元
- 小结

## const成员函数

在定义一个成员函数时，可以给它加上一个 const说明，表示它是一个获取对象状态的成员函数。例如：

```
class A
{......
    void f() const {......}
};
```

## const成员函数

函数声明和定义处都要加const

```
class A
{
    int x,y;

public:

    void f() const;
};

void A::f() const
{
    ......
}
```

## const成员函数

```
class A
{ int x;
public:
int f() const
{...
}
};
```

```
class A
{ int x;
public:
const int f()
{...
}
};
```

## const成员函数

- 在const成员函数体中不能修改数据成员的值，也不能调用该类中的非常成员函数。

![](img/6d59ef6ebdae7180bd2f8d0def48533b_491_0.png)

软件工程知识：如果成员函数不修改对象，最好将所有类成员函数声明为const。

## const成员函数

```
class A
{ int x;
    char *p;
    public:
        void f() const
        {x=10;//error
        p=new char[20];//error
        }
};
```

## const成员函数

□ const对象

软件工程知识：将对象声明为const有利于实现最低权限原则，这样试图修改对象就会产生编译时错误而非执行时错误。

□ 性能提示：把变量和对象声明为const，这不仅是一种有效的软件工程原则，而且还能提高性能，因为如今复杂的优化编译器能对常量进行某些优化，但无法对变量进行优化。

## const成员函数

只有常成员函数才有资格操作常对象。

```
class A
{ int x,y;
public:
    void f() const {...}
    void g(){...} };
const A a;
a.f(); //OK
a.g(); //error
```

## const成员函数

![](img/6d59ef6ebdae7180bd2f8d0def48533b_496_0.png)

软件工程知识：可以对 const 成员函数进行非 const 版本的重载。编译器将根据调用函数的对象性质选择相应的重载函数来使用。如果对象是 const 的，则编译器使用 const 版本的重载函数；如果对象是非 const 的，则编译器使用非 const 版本的重载函数。

## const成员函数

- □ const关键字可以被用于参与对重载函数的区分。如：
- void print();
- void print() const;

## 第四章 类与对象

- 类
- 对象
- 构造函数和析构函数
- const成员函数
- 成员对象——类的组合
- 静态成员
- 友元
- 小结

## 成员对象

```
class A
{
 int m;
 public:
 A() {m=0;}
 A(int m1) {m=m1;}
};
```

```
class B
{
 int n;
 A a;
 public:
 B() {n=0;}
 B(int n1) {n=n1;}
};
```

```
B b1,b2(1);
```

## 成员对象的初始化

在创建包含成员对象的对象时，对成员对象的初始化是由成员对象类的构造函数来实现的。默认情况下，成员对象由成员对象类的默认构造函数进行初始化。

## 成员对象的初始化

```
class A
{
    int m;

public:
    A() { m=0; }
    A(int m1) { m=m1; }
};
```

```
class B
{
    int n;

    A a;

public:
    B() { n=0; }
    B(int n1) { n=n1; }
};
B b1,b2(1);
```

## 成员对象的初始化

如需要调用成员对象的非默认构造函数对成员对象进行初始化，则要在包含成员对象的类的构造函数成员初始化表指出。

```
class A
{ int m;
    public:
        A() {m=0;}
        A(int m1)
            {m=m1;}
};
```

```
class B
{  int n;
    A a;
    public:
    B() {n=0;}
    B(int n1):a(n1) {n=n1;}
};
B b1,b2(1);
```

```
class Date
{
public:
    Date(int = 1, int = 1, int = 1900); // default constructor
    void print() const; // print date in month/day/year format
    ~Date(); // provided to confirm destruction order
private:
    int month; // 1-12 (January-December)
    int day; // 1-31 based on month
    int year; // any year
}; // end class Date
```

```
```cpp
class Employee
{
public:
Employee( const char * const, const char * const,
const Date &, const Date & );
void print() const;
~Employee(); // provided to confirm destruction order
private:
char firstName[ 25 ];
char lastName[ 25 ];
const Date birthDate; // composition: member object
const Date hireDate; // composition: member object
};
// end class Employee
```
```

```
```
Employee::Employee( const char * first, const char * last,
const Date &dateOfBirth, const Date &dateOfHire )
: birthDate( dateOfBirth ), // initialize birthDate
hireDate( dateOfHire ) // initialize hireDate
```
```

```
```
{
// copy first into firstName and be sure that it fits
int length = strlen( first );
length = ( length < 25 ? length : 24 );
......
}
```
```
