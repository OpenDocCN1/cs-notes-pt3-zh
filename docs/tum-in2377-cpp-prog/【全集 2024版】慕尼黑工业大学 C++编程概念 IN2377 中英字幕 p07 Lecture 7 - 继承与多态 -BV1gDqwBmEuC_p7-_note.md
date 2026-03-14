# C++编程概念：第7讲：继承与多态

![](img/7ac7689e80af96950a7818eefcfab600_1.png)

![](img/7ac7689e80af96950a7818eefcfab600_3.png)

![](img/7ac7689e80af96950a7818eefcfab600_5.png)

在本节课中，我们将完成面向对象编程章节的学习，重点探讨继承、多态、虚函数以及相关的注意事项。

![](img/7ac7689e80af96950a7818eefcfab600_7.png)

![](img/7ac7689e80af96950a7818eefcfab600_9.png)

![](img/7ac7689e80af96950a7818eefcfab600_10.png)

## 概述

![](img/7ac7689e80af96950a7818eefcfab600_12.png)

![](img/7ac7689e80af96950a7818eefcfab600_14.png)

上一节我们讨论了资源管理、拷贝、移动和所有权。本节中，我们将探讨面向对象编程的核心概念：继承和多态。我们将学习如何从一个类派生出新类，如何通过虚函数实现多态行为，以及在使用这些特性时需要注意的细节。

![](img/7ac7689e80af96950a7818eefcfab600_16.png)

![](img/7ac7689e80af96950a7818eefcfab600_18.png)

![](img/7ac7689e80af96950a7818eefcfab600_20.png)

## 继承基础

在C++中，可以使用`struct`或`class`关键字定义类，并可以从其他类派生新类。我们称被派生的类为基类。

![](img/7ac7689e80af96950a7818eefcfab600_22.png)

![](img/7ac7689e80af96950a7818eefcfab600_24.png)

以下是继承的基本语法：
```cpp
class Base {
    // 基类成员
};

class Derived : public Base {
    // 派生类成员
};
```

C++允许从多个基类继承，这称为多重继承。然而，多重继承可能导致复杂问题，因此除非有明确需求，否则应避免使用。

## 构造函数与析构函数

![](img/7ac7689e80af96950a7818eefcfab600_26.png)

基类在派生类中类似于高优先级的成员。在构造派生类对象时，基类构造函数首先被调用（按基类指定列表中的顺序），然后初始化派生类的数据成员，最后执行派生类构造函数的函数体。

![](img/7ac7689e80af96950a7818eefcfab600_28.png)

![](img/7ac7689e80af96950a7818eefcfab600_30.png)

基类默认调用其默认构造函数，除非在派生类的构造函数初始化列表中显式指定。

![](img/7ac7689e80af96950a7818eefcfab600_32.png)

以下是如何在派生类构造函数中委托调用基类构造函数的示例：
```cpp
class Base {
public:
    Base(int a) : value(a) {}
    int value;
};

![](img/7ac7689e80af96950a7818eefcfab600_34.png)

![](img/7ac7689e80af96950a7818eefcfab600_36.png)

![](img/7ac7689e80af96950a7818eefcfab600_38.png)

class Derived : public Base {
public:
    Derived(int a, int b) : Base(a), derived_value(b) {}
    int derived_value;
};
```

析构函数的调用顺序与构造函数相反：首先调用派生类的析构函数，然后按与构造相反的顺序调用基类的析构函数。

![](img/7ac7689e80af96950a7818eefcfab600_40.png)

## 访问修饰符与继承模式

![](img/7ac7689e80af96950a7818eefcfab600_42.png)

![](img/7ac7689e80af96950a7818eefcfab600_44.png)

在继承时，可以指定访问修饰符（`public`、`protected`、`private`）来控制基类成员在派生类中的可见性。

![](img/7ac7689e80af96950a7818eefcfab600_46.png)

*   **`public`继承**：基类的`public`成员在派生类中保持`public`，`protected`成员保持`protected`。这是最常用的模式，用于建模“是一个”的关系。
*   **`protected`继承**：基类的`public`和`protected`成员在派生类中都变为`protected`。
*   **`private`继承**：基类的`public`和`protected`成员在派生类中都变为`private`。

![](img/7ac7689e80af96950a7818eefcfab600_48.png)

`protected`和`private`继承属于特殊情况，通常很少使用。

![](img/7ac7689e80af96950a7818eefcfab600_50.png)

## 多态与虚函数

继承的一个主要目的是实现多态，即通过基类指针或引用调用派生类的特定方法。在C++中，多态不是默认行为，需要通过虚函数实现。

![](img/7ac7689e80af96950a7818eefcfab600_52.png)

![](img/7ac7689e80af96950a7818eefcfab600_54.png)

默认情况下，如果在派生类中重新定义基类的函数，它会隐藏基类版本，而不是覆盖。要实现多态，必须在基类中将函数声明为`virtual`，并在派生类中使用`override`关键字。

以下是一个示例：
```cpp
class Base {
public:
    virtual void foo() { std::cout << "Base::foo\n"; }
};

class Derived : public Base {
public:
    void foo() override { std::cout << "Derived::foo\n"; }
};
```

现在，通过基类引用调用`foo`将根据实际对象类型调用正确的函数。

## 覆盖的规则

要成功覆盖虚函数，派生类中的函数必须与基类虚函数具有相同的名称、参数列表和限定符（如`const`）。返回类型必须相同或是协变的。

使用`override`关键字至关重要，因为它能让编译器检查你是否正确覆盖了基类的虚函数，避免因拼写错误或参数不匹配而意外创建新函数。

![](img/7ac7689e80af96950a7818eefcfab600_56.png)

![](img/7ac7689e80af96950a7818eefcfab600_58.png)

## 抽象类与纯虚函数

可以将虚函数声明为纯虚函数，从而使类成为抽象类。抽象类不能实例化，但可以用作基类来定义接口。

声明纯虚函数的语法如下：
```cpp
class AbstractBase {
public:
    virtual void pureVirtual() = 0; // 纯虚函数
};
```

![](img/7ac7689e80af96950a7818eefcfab600_60.png)

派生类必须覆盖所有纯虚函数才能成为具体类。

![](img/7ac7689e80af96950a7818eefcfab600_62.png)

![](img/7ac7689e80af96950a7818eefcfab600_64.png)

![](img/7ac7689e80af96950a7818eefcfab600_66.png)

## 多态类的注意事项

![](img/7ac7689e80af96950a7818eefcfab600_68.png)

![](img/7ac7689e80af96950a7818eefcfab600_70.png)

![](img/7ac7689e80af96950a7818eefcfab600_72.png)

使用多态类时需要注意以下几点：

![](img/7ac7689e80af96950a7818eefcfab600_74.png)

![](img/7ac7689e80af96950a7818eefcfab600_76.png)

![](img/7ac7689e80af96950a7818eefcfab600_77.png)

![](img/7ac7689e80af96950a7818eefcfab600_79.png)

1.  **构造函数和析构函数中的虚函数**：在构造函数和析构函数中调用虚函数时，不会进行动态绑定，而是调用当前类（正在构造或析构的类）的版本。
2.  **虚析构函数**：如果一个类打算作为多态基类使用（即通过基类指针删除派生类对象），其析构函数必须是虚的。否则，通过基类指针删除派生类对象会导致未定义行为。
3.  **对象切片**：将派生类对象赋值给基类对象（而非指针或引用）时，派生类特有的部分会被“切掉”，只保留基类部分。这通常不是期望的行为。因此，对于多态类型，通常应禁用拷贝和移动操作（使用`= delete`）。
4.  **克隆模式**：如果需要复制多态对象，可以实现一个虚的`clone`方法，它在派生类中返回一个指向新副本的指针（通常包装在`std::unique_ptr`中）。

![](img/7ac7689e80af96950a7818eefcfab600_81.png)

## 动态类型转换

`dynamic_cast`用于在继承层次结构中进行安全的向下转型。它需要运行时类型信息（RTTI），因此只适用于具有虚函数的类。

![](img/7ac7689e80af96950a7818eefcfab600_83.png)

对于指针类型，如果转型失败，`dynamic_cast`返回`nullptr`。对于引用类型，如果转型失败，则抛出`std::bad_cast`异常。

![](img/7ac7689e80af96950a7818eefcfab600_85.png)

![](img/7ac7689e80af96950a7818eefcfab600_86.png)

## 虚函数的实现机制

![](img/7ac7689e80af96950a7818eefcfab600_88.png)

![](img/7ac7689e80af96950a7818eefcfab600_90.png)

![](img/7ac7689e80af96950a7818eefcfab600_92.png)

大多数编译器使用虚函数表（vtable）来实现动态绑定。每个多态类都有一个vtable，其中存储了指向其虚函数的指针。每个多态类的对象都包含一个指向其vtable的指针（vptr）。调用虚函数时，通过vptr找到vtable，再通过vtable中的函数指针调用正确的函数。

![](img/7ac7689e80af96950a7818eefcfab600_94.png)

![](img/7ac7689e80af96950a7818eefcfab600_96.png)

![](img/7ac7689e80af96950a7818eefcfab600_98.png)

![](img/7ac7689e80af96950a7818eefcfab600_100.png)

这种机制带来了少量开销：
*   **内存开销**：每个对象需要一个额外的vptr（通常8字节），每个类需要一个vtable。
*   **运行时开销**：每次虚函数调用需要两次间接寻址（通过vptr和函数指针）。

## 其他要点

*   **`final`关键字**：可以用于类（防止进一步派生）或虚函数（防止在派生类中被覆盖）。
*   **`std::enable_shared_from_this`**：如果一个类的方法需要返回指向自身的`std::shared_ptr`，该类应继承自`std::enable_shared_from_this`，并使用`shared_from_this()`方法。
*   **组合优于继承**：在设计中，应优先考虑组合（“有一个”关系），而不是继承（“是一个”关系）。继承应仅用于建立真正的子类型关系。

![](img/7ac7689e80af96950a7818eefcfab600_102.png)

## 总结

![](img/7ac7689e80af96950a7818eefcfab600_104.png)

本节课中我们一起学习了C++中继承与多态的核心概念。我们了解了如何通过继承建立类之间的关系，如何使用虚函数和`override`关键字实现多态行为。我们还探讨了抽象类、对象切片、虚析构函数的重要性以及克隆模式。最后，我们简要了解了虚函数的实现机制和一些设计原则，如优先使用组合。掌握这些概念对于设计和实现灵活、可扩展的面向对象程序至关重要。