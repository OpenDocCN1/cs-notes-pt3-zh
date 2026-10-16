

## 类型转换运算符

## 运算符重载

```cpp
class HighWorker {
public:
    HighWorker(float a = 2000.0){income = a;}
    operator Worker() //类型转换函数
    {Worker s; s.Getincome()=0.75*income; return(s);}
    float & Getincome(){return(income);}
private:
    float income;
};

class Worker {
public:
    Worker(float a = 1200.0){income = a;}
    Worker(HighWorker b){income = 0.75*b.Getincome();}
    //转换构造函数
    float & Getincome(){return(income);}
private:
    float income;
};

void m(Worker a){cout<<a.Getincome()<<endl;}
void main(){Worker a; m(a); HighWorker b; m(b);}
```

## 防止转换的二义性：

同一个类中定义了多个转换运算符重载函数.

```cpp
class RMB{
RMB(double value=0.0);
public:
operator double();
operator float();
//....
};
int main()
{RMB d1(2.0),d2(1.5),d3;
d3=d1+d2; //error
d3=double(d1)+double(d2);
return 0;
}
```

## 运算符重载

只能是成员的运算符: (系统为类提供的)
=、 ( )、 []、 ->

只能是友元的运算符: (cout是其它类的对象)
cout<<、 cin>>

既可以友元也可以成员的: (定义者提供)
+、 - 等

## 第七章 继承

```cpp
class Student{
int move_tel;
public:
int id;
string name;
protected:
int tel;
};
```

class 派生类名：继承方式 基类名 { 派生类中的新成员 }

```cpp
class Master :public Student{
string topic;
public:
string dept;
protected:
string major;
};
```

```cpp
void main() { Master a; }
```

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_232_0.png)

派生类继承了基类的除了构造函数、析构函数、拷贝构造函数和赋值运算符重载函数之外的所有成员，因此派生类对象由两部分组成：一部分是由基类继承的成员，另一部分是派生类新增加的自己特有的成员。

当类的继承方式为公有继承时，基类的公有和保护成员的访问属性在派生类中不变，而基类的私有成员不可访问。

访问：函数访问数据成员&函数访问函数。直接和间接

### 父类

### 继承

### 派生类

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_233_0.png)

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_233_1.png)

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_233_2.png)

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_233_3.png)

## 继承

```cpp
class Student{
    int m3;
    public:
        int m1; void x(){m1=1;m2=2;m3=3;}
    protected:
        int m2;
};
class Master :public Student{
    int n3;
    public:
        void y(){m1=1;m2=2;m3=3;n1=1;n2=2;n3=3;}  //对内
        void z(){x();}  //间接访问了父类的private成员
        int n1;
    protected:
        int n2;
};
void main()
{ Master a;
    a.m1=1;a.m2=2;a.m3=3;a.n1=1;a.n2=2;a.n3=3;  //对外
    a.x();
    a.z();
}
```

## 继承

继承的本质实际上就是由上到下完全的复制；但是在对内可见性上做了手脚，对外可见性则没有改变。

C++提供了类的继承机制，解决了软件的复用问题。

自动的、滚动式的重用代码，增强代码，使得编程方式根本转变，分析问题、解决问题的模式从功能模式转向面向对象的结构模式

## 继承

类的继承和派生的层次结构是人们对自然界中的事物进行分类、分析和认识的过程在程序设计中的体现。

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_236_0.png)

- 继承的方式使得新事物的描述更简单
- 例如：已知鸟的属性，鸭子是什么的描述便可以在鸟的基础上进行：
  - 除了是鸟之外，还会一种区别于其他鸟的特殊的嘎嘎叫。
  - 因为鸭子不会飞，于是就在继承鸟的属性中去掉会飞的属性。

```
//多级派生
class Student{
public:
    int m1;
protected:
    int m2;
private:
    int m3;
};
class Master :public Student
{
public:
    int n1;
protected:
    int n2;
private:
    int n3;
};
```

```cpp
class MasterEnginee :public Master{
public:
    int p1;
protected:
    int p2;
private:
    int p3;
};
```

```cpp
void main()
{ MasterEnginee a;
}
```

直接基类：直接参与派生出某类的基类。
间接基类：基类的基类，甚至更高层的基类。
直接派生类
间接派生类

赋值兼容规则是指需要基类对象的任何地方都可以**使用公有派生类的对象来替代**。替代之后，派生类对象就可以作为基类的对象使用，但**只能使用从基类继承的成员**。

里氏代换原则：
(LSP-Liskov Substitution Principle)
在软件里面，把基类都替换成它的子类，程序的行为没有变化。

## 允许将派生类的对象赋值给基类的对象。

拷贝派生类的基类子对象

从基类继承的数据成员

派生类新增的数据成员

派生类对象的其余部分

派生类对象内存映射

```cpp
class Student{
public:  int m1;
void x(){m1=1;m2=2;m3=3;}
protected:  int m2;
private:  int m3;};
class Master :public Student{
public:
void y(){m1=1;m2=2;n1=1;n2=2;n3=3;}
int n1;
protected: int n2;
private: int n3;
};
void f(Student a){a.m1=5;a.n1=6;a.x();a.y();}
void main()
{ Master a;
f(a); //派生类的对象可以赋值给基类对象
Student *p=&a;p->m1=1;p->n1=2;p->x();p->y();
//基类的指针可以指向派生类的对象
Student &q=a;q.m1=1;q.n1=2;q.x();q.y(); }
//派生类的对象初始化基类的引用
```

使用时还应注意：当派生类对象赋值给基类对象或基类指针后，只能通过基类名或基类指针访问派生类中从基类继承来的成员，不能访问派生类中的其它成员。

说明派生类对象包含父类对象全部内容凡是父类对象可以出现的地方可以用子类对象代替，反之不可

## 不允许将基类的对象赋值给派生类的对象。

基类对象内存映像

派生类对象内存映像

从基类对象拷贝的继承的数据成员

与基类对象无关的不确定信息

```cpp
class Student{
    int m3;
    public: int m1; void x(){m1=1;m2=2;m3=3;}
    protected: int m2;
};
class Master :public Student{
    int n3;
    public: int n1; void y(){m1=1;m2=2;n1=1;n2=2;n3=3;}
    protected: int n2;
};
void f(Master &a){... ...;}
void main()
{ Student a; Master b;
    f(a);
    Master *p=&a;
    b = a;
}
```

继承

子类对象不可以
用父类对象代替

