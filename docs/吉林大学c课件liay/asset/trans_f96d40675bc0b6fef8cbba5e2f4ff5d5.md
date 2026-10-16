
## 9. 引入虚函数支持多态

```
class Automobile{
public:
//...
virtual void Run(){
    cout<< "机械变速" <<endl;
}
};

class Car:public Automobile{
public:
//...
virtual void Run(){
    cout<< "自动变速" <<endl;
}
};
```

```
void Fn(Automobile *p){
    p->Run();
}

void main(){
    Fn(new Automobile);
    Fn(new Car);
}
```

机械变速
自动变速

派生类中的函数只要原型相同，则自动具有虚函数性质，其virtual关键字可省略

## 虚函数的使用方法：

- （1） 在基类用virtual声明成员函数为虚函数
- （2） 在派生类中重新定义此函数，要求函数名、函数的参数个数和类型全部与基类的虚函数相同，并根据派生类的需要重新定义函数体。
- （3） 定义一个指向基类对象的指针变量，并使它指向同一类族中的某一对象。
- （4） 通过该指针变量调用此虚函数，此时调用的就是指针变量指向的对象的同名函数。

C++规定，当一个成员函数被声明为虚函数后，其派生类中原型相同的函数都自动成为虚函数 派生类没有对基类的虚函数重新定义，则派生类继承其直接基类的虚函数

## 类型转换：

static_cast:静态转型，必须是相关类型，非多态类层次的祖孙互易，void*转换任何类型，

dynamic_cast: 动态转型，专门针对有虚函数的继承结构，将基类指针转换成想要的子类指针

const_cast: 常量转型，去掉常量性的转换。

```
使用： dynamic_cast<Derived*>(p);
    static_cast<Car*>(p);
    const char* max(const char*,const char*);
char*
    p=const_cast<char*>(max("hello","good"));
```

## vector是C++STL(标准模板类库)的重要一员。可以容纳许多其它类型的相同实体，称为容器。

使用时：`#include<vector>`

四种定义方式：

- (1) `vector<int>a(10);`
- (2) `vector<int>b(10,1);`
- (3) `vector<int>c(b);`
- (4) `vector<int>d(b.begin(),b.begin()+3);`

输出向量中的所有元素：

```
for(int i=0; i<a.size(); ++i)
    cout<<a[i];

for (vector<int>::iterator it=a.begin();it!=a.end();++it)
    cout<<*it;
```

`vector<int>::iterator` //遍历器，迭代器（指向容器元素的指针）

向量中的操作都是通过使用成员函数来完成的：

```
a.clear();
a.assign(4,2);//a有0-3个元素，值为2
a.push_back(5);
a.resize(10,2)//元素的个数调整至10个，值为2
```

## 10. 多态编程体验

```
class Shape{
    public:
    // ...
    virtual double area(){}
};
class Circle:public Shape{
    public:
    double area(){...}
    // ...
};
class Triangle:public Shape{
    public:
    double area(){...}
    // ...
};
// ...
//类定义由程序员A完成
```

```
vector<Shape*> a (100);
void Fn(){
    a[0] = new Circle;
    a[1] = new Triangle;
    a[2] = new X;
    // ...
}//本函数由程序员B完成
```

```
double Sum(){
    double s = 0;
    for(int i=0; i<a.size(); ++i)
        s = s+a[i]->area();
    return(s);
} //本函数由程序员C完成
```

## 11. 虚函数的实用意义：

从基类继承来的某些成员函数不完全适应派生类的需要，允许其派生类中对该函数重新定义，赋予它新的功能，当基类的这些成员函数声明为虚函数后，可以通过指向其基类的指针指向同一类族中不同类的对象，从而调用其同名的函数。由虚函数实现的多态性是：同一类族中不同类的对象，对同一函数调用作出不同的响应。

是追求用指针管理继承体系对象的结果。
多态性使得应用程序使用类体系中的不同层次对象,并使这些对象共存的复杂局面达到了一种可管理的境界。
程序员从使用孤立的类，到使用分层的类，并且让各种对象“同场竞技”，充分展现其个性。

## 12. 多态应用的三种场景

```
class X{
public:
    virtual void f1(){cout<<"Running X::f1()"<<endl;f4();}
    virtual void f2(){cout<<"Running X::f2()"<<endl;f3();}
    virtual void f3(){cout<<"Running X::f3()"<<endl;f4();}
    virtual void f4(){cout<<"Running X::f4()"<<endl;}
};
class Y:public X{
public:
    void f1(){cout<<"Running Y::f1()"<<endl;f2();}
    void f3(){cout<<"Running Y::f3()"<<endl;f4();}
};
void main(){
    X &p = *(new Y);
    p.f1();
}
（指针、引用、成员函数）
```

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_292_0.png)

## 13. 多态的实现

联编（编联、束定、绑定）(binding)：就是把一个标识符名称和一个存储地址联系在一起的过程。将一个函数调用链接上相应于函数体的代码，这一过程就是函数联编。应将其理解为：在调用同名函数时，确定用其中的哪一个函数来执行的过程。

静态联编：出现在运行前的联编（在编译时完成），也称为早期联编。

动态联编：联编工作在程序运行阶段完成的情况。在编译、连接过程中无法解决的联编问题，要等到程序开始运行之后再来确定。也称为滞后联编。

## 虚函数的工作机理

Virtual出现则每个类增加一个虚函数表保存类的虚函数

凡有虚函数的类均维护一个虚函数表

实例化每个对象中会增加一个指针指向虚函数表（对象大小会有变化）。

虚函数调用时不需要确定对象类型，通过该指针即可找到所要链接函数

```
class A{
    public:
        virtual void f();
        virtual void g(int);
        virtual void h(double);
    private:
        int a;
};
class B:public A{
    public:
        virtual void g(int);
    private:
        int b;};
class C:public B{
    public:
        virtual void h(double);
    private:
        int c;
};
```

## 虚函数的工作机理

### A的虚拟表

### C的虚拟表

Vptr a

&A::f[0]
&A::g[1]
&A::h[2]

Vptr a b c

&A::f[0]
&B::g[1]
&C::h[2]

### A类对象的存储布局

### C类对象的存储布局

### B的虚拟表

Vptr a b

&A::f[0]
&B::g[1]
&A::h[2]

### B类对象的存储布局

Vptr指向vtbl的开始地址，所有vtbl有相同的顺序。

## 虚函数的工作机理

对虚函数的调用C++编译器转换为一个间接调用。

例如，
A* pa;
pa->h(5);

转换为：
对pa->vptr[2]的调用

如果pa指向一个A类对象，则调用A::h()。
如果pa指向一个C类对象，则调用C::h()。

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_297_0.png)

![](img/2a27c9e9d8641bba50c8f3e0109e4e84_297_1.png)

