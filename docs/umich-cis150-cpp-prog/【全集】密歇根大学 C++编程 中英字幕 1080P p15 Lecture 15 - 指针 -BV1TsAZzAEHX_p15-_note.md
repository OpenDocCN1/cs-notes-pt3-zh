# C++编程：15：指针与动态内存管理

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_0.png)

在本节课中，我们将学习C++中指针的核心概念，包括动态内存的分配与释放、指针与对象的关系，以及继承和多态性的初步介绍。理解这些概念对于编写高效、灵活的C++程序至关重要。

## 动态内存分配与释放

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_2.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_4.png)

上一节我们介绍了使用代码模拟现实场景的优势。本节中我们来看看如何通过动态内存管理来增强程序的灵活性。

当我们在程序中使用 `new` 关键字时，是在向操作系统请求在**堆**上分配内存。堆是一个比栈大得多的内存池，栈的空间在程序启动时就已预先分配好。

**核心公式：**
```cpp
int* ptr = new int; // 在堆上分配一个整数的内存
```

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_6.png)

使用 `new` 分配内存后，我们必须在使用完毕后手动释放它，否则会导致内存泄漏。释放内存使用 `delete` 关键字。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_8.png)

**核心公式：**
```cpp
delete ptr; // 释放单个指针指向的内存
delete[] arrayPtr; // 释放动态数组的内存
```

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_10.png)

对于动态数组，必须使用 `delete[]` 而非 `delete`。如果忘记释放内存，程序占用的内存会持续增长。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_12.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_14.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_16.png)

## 指针与对象

指针不仅可以指向基本数据类型，也可以指向类的对象。这使得我们可以在堆上创建对象。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_18.png)

当我们使用指针访问对象的成员函数时，语法与普通对象不同。需要使用箭头操作符 `->` 而非点操作符 `.`。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_20.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_22.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_24.png)

**核心代码示例：**
```cpp
Chair* ericsChair = new Chair(); // 在堆上创建一个Chair对象
ericsChair->setColor("blue"); // 使用箭头操作符调用成员函数

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_26.png)

Chair jebsChair; // 在栈上创建一个Chair对象
jebsChair.setColor("black"); // 使用点操作符调用成员函数
```

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_28.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_30.png)

虽然目前看来在堆上创建单个对象优势不明显，但随着程序复杂度增加，堆内存的管理能力将变得非常重要。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_32.png)

## 继承简介

继承是面向对象编程的核心原则之一，它允许我们创建一个新类（子类）来继承现有类（父类）的属性和行为。这就像生物学中的遗传，子类继承了父类的特性，同时可以添加自己独有的特性。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_34.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_35.png)

例如，我们可以有一个基础的 `Chair` 类。如果我们想要一个带马达的椅子，无需重写整个 `Chair` 类，只需创建一个继承自 `Chair` 的 `MotorizedChair` 类，并添加驱动功能即可。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_37.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_39.png)

**核心代码示例：**
```cpp
class MotorizedChair : public Chair { // MotorizedChair 继承自 Chair
public:
    void drive() {
        cout << "vroom" << endl;
    }
};

class FloatingChair : public Chair { // FloatingChair 继承自 Chair
public:
    void drive() {
        cout << "splash" << endl;
    }
};
```

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_41.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_42.png)

## 多态性与虚函数

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_44.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_46.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_48.png)

继承的一个强大特性是**多态性**。它允许我们使用父类的指针或引用来操作子类的对象，并在运行时决定调用哪个版本的函数。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_50.png)

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_52.png)

为了实现多态性，我们需要在父类中将函数声明为 `virtual`（虚函数），并在子类中使用 `override` 关键字来重写该函数。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_54.png)

**核心代码示例：**
```cpp
class Chair {
public:
    virtual void drive() { // 声明为虚函数
        // 普通椅子不能驱动，什么都不做
    }
};

void driveChair(Chair* aChair) {
    aChair->drive(); // 根据实际对象类型调用正确的 drive 函数
}
```

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_56.png)

当我们调用 `driveChair` 并传入一个 `MotorizedChair` 指针时，程序会在运行时识别出它实际上是 `MotorizedChair` 类型，从而调用 `MotorizedChair::drive()` 输出 “vroom”，而不是父类中什么都不做的版本。这就是多态性的魔力。

如果没有指针，这种运行时行为解析将无法实现。多态性允许我们编写更通用、更灵活的代码，例如，一个函数只需要知道对象“可以驱动”，而不必关心它具体是哪种椅子。

## 总结与后续

本节课中我们一起学习了C++指针的几个关键方面：
1.  使用 `new` 和 `delete` 进行动态内存的手动管理。
2.  指针与对象结合使用时，需使用 `->` 操作符。
3.  继承的基本概念，允许子类扩展父类的功能。
4.  多态性的初步介绍，通过虚函数和重写，实现运行时函数调用的动态绑定。

指针是C++强大但也容易出错的特性。现代C++推荐使用智能指针（如 `unique_ptr`, `shared_ptr`）来自动管理内存，减少内存泄漏的风险。此外，关于拷贝构造函数、赋值运算符和析构函数的“三法则”，我们将在后续课程中深入探讨。

![](img/e6d154982b8a44dcdbf0ef77b8fd2046_58.png)

掌握指针和动态内存是深入理解C++的重要一步，它们为构建复杂、高效的程序奠定了基础。