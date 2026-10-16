

## 将 Ival_box 设计为一个抽象界面

```
class Ival_box {
public:
    virtual int get_value() = 0;
    virtual void set_value(int i) = 0;
    virtual void reset_value(int i) = 0;
    virtual void prompt() = 0;
    virtual bool was_changed() const = 0;
    virtual ~Ival_box() {}
};

class Ival_slider : public Ival_box,
                    protected BBwindow
{
public:
    Ival_slider(int, int);
    ~Ival_slider();
    int get_value();
    void set_value(int i);
    //...
protected:
    //...
```

## 其他

- 虚析构函数最好用在需要清理工作的类中；这样，用户就可以通过基类指针调用派生类的析构函数。
- 现在的类层次结构如下：

```
class Ival_box { /*...*/ };
class Ival_slider : public Ival_box, protected BBwindow { /*...*/ };
class Ival_dial : public Ival_box, protected BBwindow { /*...*/ };
class Flashing_ival_slider : public Ival_slider { /*...*/ };
class Popup_ival_slider : public Ival_slider { /*...*/ };
```

### 12.4.3 其他实现方式

- 与传统方式相比，这种设计更加清晰，也更容易维护，而且并不低效。
- 但它没有解决版本控制问题。
- 一个明显的解决方案是采用不同的名字，定义几个不同的 Ival_slider：

```
class Ival_box { /*...*/ };
class Ival_slider : public Ival_box, protected BBwindow { /*...*/ };
class BB_ival_slider : public Ival_box, protected BBwindow { /*...*/ };
```

## 其他实现方式(2)

- 更进一步，可以将 Ival_box 与实现细节隔离开来，从 Ival_box 派生出一个抽象的 Ival_slider 类，然后从它派生出针对各个系统的 Ival_slider 类。
- 通常还可以利用实现层次结构中的某些更专门的类，把设计做得更好。

```
class Ival_box { /*...*/ };
class Ival_slider : public Ival_box, protected BBwindow { /*...*/ };
class CW_ival_slider : public Ival_slider, protected CWslider { /*...*/ };

class BB_ival_slider : public Ival_slider, protected BBslider { /*...*/ };
class CW_ival_slider : public Ival_slider, protected CWslider { /*...*/ };
```

## 其他实现方式(3)

最终，完整的类层次结构可以是我们原来的面向应用的接口层次结构与各界面实现层次结构的结合。

```
class Ival_box { ... };
class Ival_box : public Ival_box { ... };
class Ival_dial : public Ival_box { ... };
class Flashing_ival_slider : public Ival_slider { ... };
class Popup_ival_slider : public Ival_slider { ... };

class BB_ival_slider : public Ival_slider, protected BBSlider { ... };
class BB_flashing_ival_slider : public Flashing_ival_slider, protected BBWindow_with_bells_and_whistles { ... };
class BB_popup_ival_slider : public Popup_ival_slider, protected BBSlider { ... };

class CW_ival_slider : public Ival_slider, protected CWSlider { ... };
```

### 12.4.3.1 评论

这种抽象类设计非常灵活，而且与那种依赖于一个定义用户界面系统的公共基类的等价设计相比，处理起来几乎同样容易。

从应用的角度看，这两种设计是等价的；几乎所有的代码都能不加修改，以同样的方式使用。

使用抽象类设计，几乎所有的用户代码都得到了保护，能够抵御实现层次结构的变化，而且在这种变化之后不需要重新编译。

## 12.4.4 对象创建的局部化

对象的创建必须通过特定于实现的类名来完成，例如 CW_ival_dial 和 BB_flashing_ival_slider。我们希望尽可能减少这些特定名称出现的位置。

解决方法是引入一个接口（可以通过多种方式实现）。一种简单的方式是引入一个抽象类，用来表示一组创建操作：

```
class Ival_maker {
public:
    virtual Ival_dial* dial(int)=0; // 纯虚函数
    virtual Popup_ival_slider* popup_ival_slider(int,int)=0;
}; // 这个类被称为一个工厂(factory)。它的存在有时被称为
// 强制的编译时多态(运行时多态)
```

## 对象创建的局部化

```
class BB_maker : public Ival_maker // 假BB版本
{
public:
    Ival_dial* dial(int);
    Popup_ival_slider*
    popup_ival_slider(int,int);
};
class LS_maker : public Ival_maker // 假LS版本
{
public:
    Ival_dial* dial(int);
    Popup_ival_slider*
    popup_ival_slider(int,int);
};
```

## 对象创建的局部化

```
Ival_dial* BB_maker::dial(int a, int b)
{
    return new BB_ival_dial(a,b);
}

Ival_dial* LS_maker::dial(int a, int b)
{
    return new LS_ival_dial(a,b);
}

void user(Ival_maker* pim)
{
    Ival_box* pb=pim->dial(0,99);
    ...
}

BB_maker BB_impl;
// 为BB
LS_maker LS_impl;
// 为LS
void driver()
{
    user(&BB_impl);
    user(&LS_impl);
}
// 为LS
```

## 12.5 类层次结构和抽象类

- 一个抽象类就是一个界面。
- 类层次结构是一种逐步建立类的方式；其中的类一方面为用户提供有用的功能，另一方面也作为实现更高级或更专门类的构造基块。这种层次结构非常适合以逐步求精方式进行的程序设计。
- 抽象类的层次结构是清晰而有力地表达概念的方法，不会被实现细节或运行时开销所模糊。

## 类层次结构和抽象类

- 虚函数调用是廉价的，与它所跨越的抽象边界种类无关；调用抽象类的成员函数时，与调用任何其他虚函数一样，具有完全相同的优化余地。
- 结论：一个系统展现给用户的应当是一个抽象类的层次结构，而其实现所使用的则是一个传统的层次结构。

## 12.6 忠告

- [1] 避免类层次结构。
- [2] 用指针和引用避免切割问题。
- [3] 用抽象类把设计集中在提供清晰的界面上。
- [4] 用类层次结构使代码复制量最小化。
- [5] 用抽象类使用户免受实现细节的影响。
- [6] 用虚函数使实现可以更新，而又不影响用户代码。
- [7] 用层次结构减少代码复制。
- [8] 用抽象类使不同的实现能够共存。
- [9] 有虚函数的类应当有虚析构函数。
- [10] 抽象类通常不需要拷贝构造函数。
- [11] 同一个概念可以采用不同的表示。

