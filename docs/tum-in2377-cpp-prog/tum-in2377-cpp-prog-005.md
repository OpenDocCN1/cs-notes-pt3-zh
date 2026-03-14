# 005：资源管理

![](img/e117ecb35c9d55ed6eb3400c243982f0_1.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_3.png)

在本节课中，我们将学习C++中的类与对象，这是面向对象编程的基础。我们将重点探讨构造函数、析构函数以及运算符重载，这些概念对于理解下一周的内存和资源管理至关重要。

---

![](img/e117ecb35c9d55ed6eb3400c243982f0_5.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_7.png)

## 类与结构体

![](img/e117ecb35c9d55ed6eb3400c243982f0_9.png)

在C++中，我们使用`class`或`struct`关键字来定义用户自定义类型，它们本质上都是类。两者的主要区别在于默认的成员访问控制权限。

*   `class`的默认访问权限是`private`。
*   `struct`的默认访问权限是`public`。

![](img/e117ecb35c9d55ed6eb3400c243982f0_11.png)

定义一个类的基本语法如下：
```cpp
class ClassName {
    // 成员声明（变量、函数、类型）
}; // 注意：类定义末尾需要分号
```

![](img/e117ecb35c9d55ed6eb3400c243982f0_13.png)

---

![](img/e117ecb35c9d55ed6eb3400c243982f0_15.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_17.png)

## 类成员

![](img/e117ecb35c9d55ed6eb3400c243982f0_19.png)

类可以包含数据成员和成员函数。

![](img/e117ecb35c9d55ed6eb3400c243982f0_21.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_23.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_25.png)

### 数据成员

![](img/e117ecb35c9d55ed6eb3400c243982f0_27.png)

数据成员是类中声明的变量。它们可以是任何完整类型，并且可以使用修饰符如`static`、`const`或`thread_local`。

![](img/e117ecb35c9d55ed6eb3400c243982f0_29.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_31.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_33.png)

**示例：**
```cpp
struct Foo {
    int i = 42;          // 普通数据成员，带初始化
    std::string s{"hello"};
    static int magic_value; // 静态数据成员
    const int c = 100;   // 常量数据成员
};
```
静态数据成员属于类本身，而不是类的某个对象，因此需要在类外单独定义以分配存储空间：
```cpp
int Foo::magic_value = 0; // 静态成员的定义
```

![](img/e117ecb35c9d55ed6eb3400c243982f0_35.png)

### 成员函数

成员函数是定义在类作用域内的函数。它们可以访问类的数据成员和其他成员函数。

成员函数可以在类内直接定义（内联），也可以在类外定义（外联）。通常，我们将类声明放在头文件（`.hpp`）中，而将成员函数的定义放在源文件（`.cpp`）中，以提高编译效率。

![](img/e117ecb35c9d55ed6eb3400c243982f0_37.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_39.png)

**示例：**
```cpp
// 头文件 foo.hpp
class Foo {
public:
    void do_something(); // 声明
    int get_value() const { return value_; } // 内联定义
private:
    int value_;
};

![](img/e117ecb35c9d55ed6eb3400c243982f0_41.png)

// 源文件 foo.cpp
#include "foo.hpp"
void Foo::do_something() { // 外联定义
    // 函数实现
}
```

---

![](img/e117ecb35c9d55ed6eb3400c243982f0_43.png)

## 访问控制与`this`指针

类成员可以具有三种访问权限：
*   `public`：可以被任何代码访问。
*   `private`：只能被类自身的成员函数和友元访问。
*   `protected`：类似于`private`，但允许派生类访问。

![](img/e117ecb35c9d55ed6eb3400c243982f0_45.png)

非静态成员函数内部有一个隐式的`this`指针，它指向调用该成员函数的对象实例。通过`this`指针，可以访问当前对象的成员。

**示例：**
```cpp
class MyClass {
    int x;
public:
    void set_x(int val) {
        this->x = val; // 使用 this 指针访问成员
        // 等价于 x = val;
    }
};
```

---

![](img/e117ecb35c9d55ed6eb3400c243982f0_47.png)

## 特殊成员函数

### 构造函数

构造函数是一种特殊的成员函数，在创建类对象时自动调用，用于初始化对象。它的名称与类名相同，没有返回类型。

![](img/e117ecb35c9d55ed6eb3400c243982f0_49.png)

*   **默认构造函数**：没有参数或所有参数都有默认值的构造函数。
*   **初始化列表**：构造函数可以使用初始化列表来初始化成员变量，这发生在构造函数体执行之前。
*   **转换构造函数**：只接受一个参数的构造函数，可以用于隐式类型转换。使用`explicit`关键字可以禁止隐式转换。
*   **拷贝构造函数**：接受一个`const`引用到同类对象的构造函数，用于用一个已存在的对象初始化新对象。

![](img/e117ecb35c9d55ed6eb3400c243982f0_51.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_53.png)

**示例：**
```cpp
class Example {
    int a, b;
public:
    Example() : a(0), b(0) {} // 默认构造函数
    Example(int x, int y) : a(x), b(y) {} // 带参构造函数
    explicit Example(int x) : a(x), b(0) {} // explicit 转换构造函数
    Example(const Example& other) : a(other.a), b(other.b) {} // 拷贝构造函数
};
```

![](img/e117ecb35c9d55ed6eb3400c243982f0_55.png)

### 析构函数

析构函数在对象生命周期结束时自动调用，用于清理资源（如关闭文件、释放内存等）。它的名称是类名前加`~`，没有参数和返回类型。

![](img/e117ecb35c9d55ed6eb3400c243982f0_57.png)

对象的构造和析构顺序相反：成员变量按声明顺序构造，按逆序析构；基类先于派生类构造，晚于派生类析构。

![](img/e117ecb35c9d55ed6eb3400c243982f0_59.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_61.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_63.png)

**示例：**
```cpp
class FileHandler {
    FILE* file_;
public:
    FileHandler(const char* filename) { file_ = fopen(filename, "r"); }
    ~FileHandler() { if (file_) fclose(file_); } // 析构时关闭文件
};
```

![](img/e117ecb35c9d55ed6eb3400c243982f0_65.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_67.png)

---

![](img/e117ecb35c9d55ed6eb3400c243982f0_69.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_71.png)

## 运算符重载

![](img/e117ecb35c9d55ed6eb3400c243982f0_73.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_75.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_77.png)

C++允许重载大部分运算符，使其能用于用户自定义类型，这可以让代码更直观。运算符重载本质上是一个特殊命名的函数。

**语法：**
```cpp
ReturnType operator Op (ArgumentList) {
    // 实现
}
```

![](img/e117ecb35c9d55ed6eb3400c243982f0_79.png)

**示例：重载`+`和`==`运算符**
```cpp
class Complex {
    double real, imag;
public:
    Complex operator+(const Complex& other) const {
        return Complex(real + other.real, imag + other.imag);
    }
    bool operator==(const Complex& other) const {
        return real == other.real && imag == other.imag;
    }
};
```

![](img/e117ecb35c9d55ed6eb3400c243982f0_81.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_83.png)

可以重载的运算符包括算术运算符、关系运算符、赋值运算符、下标运算符`[]`、函数调用运算符`()`等。不能重载的运算符包括作用域解析符`::`、成员访问符`.`、`sizeof`等。

![](img/e117ecb35c9d55ed6eb3400c243982f0_85.png)

**注意**：重载运算符时应遵循其直观含义，避免造成混淆。

![](img/e117ecb35c9d55ed6eb3400c243982f0_87.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_88.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_90.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_92.png)

---

![](img/e117ecb35c9d55ed6eb3400c243982f0_94.png)

## 枚举类

![](img/e117ecb35c9d55ed6eb3400c243982f0_96.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_98.png)

`enum class`（有作用域枚举）是C++11引入的类型安全的枚举。与传统的C风格`enum`相比，它的枚举值位于枚举类的作用域内，不会隐式转换为整数，避免了命名冲突。

![](img/e117ecb35c9d55ed6eb3400c243982f0_100.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_102.png)

**示例：**
```cpp
enum class TrafficLight { Red, Yellow, Green };
TrafficLight light = TrafficLight::Red; // 必须使用作用域
// int val = light; // 错误：不能隐式转换
int val = static_cast<int>(light); // 正确：显式转换
```

![](img/e117ecb35c9d55ed6eb3400c243982f0_104.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_106.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_108.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_109.png)

建议在新代码中使用`enum class`代替普通的`enum`。

![](img/e117ecb35c9d55ed6eb3400c243982f0_111.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_113.png)

---

![](img/e117ecb35c9d55ed6eb3400c243982f0_115.png)

## 总结

![](img/e117ecb35c9d55ed6eb3400c243982f0_117.png)

![](img/e117ecb35c9d55ed6eb3400c243982f0_119.png)

本节课我们一起学习了C++中面向对象编程的核心概念。我们了解了如何使用`class`和`struct`定义类型，以及如何通过构造函数和析构函数管理对象的生命周期。我们还探讨了运算符重载，它允许我们为用户自定义类型定义直观的操作。最后，我们介绍了更安全的`enum class`枚举类型。掌握这些知识是理解下一周内存与资源管理内容的重要基础。