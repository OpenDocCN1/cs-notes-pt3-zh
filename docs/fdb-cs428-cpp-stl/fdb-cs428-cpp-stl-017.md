# 017：函数指针和成员函数指针 🧭

![](img/fe83c9eb79a2f981ea56556877891722_1.png)

![](img/fe83c9eb79a2f981ea56556877891722_3.png)

在本节课中，我们将要学习C++中的函数指针和成员函数指针。这些概念是理解C++标准模板库（STL）中**函数对象**（或称仿函数）的基础。函数指针允许我们将函数作为数据来处理，为算法和容器的灵活配置提供了可能。

![](img/fe83c9eb79a2f981ea56556877891722_5.png)

![](img/fe83c9eb79a2f981ea56556877891722_6.png)

![](img/fe83c9eb79a2f981ea56556877891722_8.png)

![](img/fe83c9eb79a2f981ea56556877891722_10.png)

## 概述：函数指针与策略模式

![](img/fe83c9eb79a2f981ea56556877891722_12.png)

函数指针是C++ STL中仿函数功能的概念基础。仿函数本质上应用了**策略模式**，使得我们能够在不改变算法或容器内部实现细节的情况下，指导和修改它们的行为。

![](img/fe83c9eb79a2f981ea56556877891722_13.png)

![](img/fe83c9eb79a2f981ea56556877891722_14.png)

![](img/fe83c9eb79a2f981ea56556877891722_15.png)

![](img/fe83c9eb79a2f981ea56556877891722_16.png)

![](img/fe83c9eb79a2f981ea56556877891722_17.png)

![](img/fe83c9eb79a2f981ea56556877891722_19.png)

![](img/fe83c9eb79a2f981ea56556877891722_20.png)

![](img/fe83c9eb79a2f981ea56556877891722_21.png)

![](img/fe83c9eb79a2f981ea56556877891722_22.png)

![](img/fe83c9eb79a2f981ea56556877891722_23.png)

上一节我们介绍了课程背景，本节中我们来看看函数指针的具体概念。

![](img/fe83c9eb79a2f981ea56556877891722_25.png)

![](img/fe83c9eb79a2f981ea56556877891722_26.png)

![](img/fe83c9eb79a2f981ea56556877891722_27.png)

![](img/fe83c9eb79a2f981ea56556877891722_28.png)

## 什么是函数指针？ 🎯

![](img/fe83c9eb79a2f981ea56556877891722_30.png)

![](img/fe83c9eb79a2f981ea56556877891722_31.png)

![](img/fe83c9eb79a2f981ea56556877891722_32.png)

![](img/fe83c9eb79a2f981ea56556877891722_33.png)

顾名思义，函数指针是一个指针变量，它存储了函数的地址。

![](img/fe83c9eb79a2f981ea56556877891722_35.png)

![](img/fe83c9eb79a2f981ea56556877891722_36.png)

程序运行时，包含数据和代码。函数是代码空间的一部分。我们可以通过函数的名称（标签）获取其地址，并将其存储起来。这样，我们就不必在源代码中硬编码调用哪个函数，而是在运行时动态决定。

![](img/fe83c9eb79a2f981ea56556877891722_38.png)

![](img/fe83c9eb79a2f981ea56556877891722_39.png)

![](img/fe83c9eb79a2f981ea56556877891722_40.png)

![](img/fe83c9eb79a2f981ea56556877891722_41.png)

![](img/fe83c9eb79a2f981ea56556877891722_42.png)

![](img/fe83c9eb79a2f981ea56556877891722_43.png)

函数指针在C语言中就已存在，并延续到C++中。它们有多种用途，例如：
*   作为`qsort`等函数的比较回调函数。
*   用于线程库（如Pthreads）或窗口系统中的回调函数和定时器。
*   C++编译器使用函数指针表来实现虚函数的分发机制。

![](img/fe83c9eb79a2f981ea56556877891722_45.png)

![](img/fe83c9eb79a2f981ea56556877891722_46.png)

## 基础函数指针示例

![](img/fe83c9eb79a2f981ea56556877891722_48.png)

![](img/fe83c9eb79a2f981ea56556877891722_49.png)

![](img/fe83c9eb79a2f981ea56556877891722_50.png)

![](img/fe83c9eb79a2f981ea56556877891722_51.png)

![](img/fe83c9eb79a2f981ea56556877891722_52.png)

让我们通过一个简单的例子来理解函数指针。首先，我们看一个不使用函数指针的版本。

![](img/fe83c9eb79a2f981ea56556877891722_54.png)

![](img/fe83c9eb79a2f981ea56556877891722_55.png)

![](img/fe83c9eb79a2f981ea56556877891722_56.png)

![](img/fe83c9eb79a2f981ea56556877891722_58.png)

我们定义了四个基础的算术运算函数：
```cpp
float plus(float a, float b) { return a + b; }
float minus(float a, float b) { return a - b; }
float multiply(float a, float b) { return a * b; }
float divide(float a, float b) { return a / b; }
```

![](img/fe83c9eb79a2f981ea56556877891722_59.png)

![](img/fe83c9eb79a2f981ea56556877891722_61.png)

![](img/fe83c9eb79a2f981ea56556877891722_63.png)

![](img/fe83c9eb79a2f981ea56556877891722_65.png)

![](img/fe83c9eb79a2f981ea56556877891722_66.png)

![](img/fe83c9eb79a2f981ea56556877891722_67.png)

然后，我们编写一个`Switch`函数，根据传入的操作码字符来调用对应的函数：
```cpp
float Switch(float a, float b, char opCode) {
    float result = 0.0;
    switch(opCode) {
        case '+': result = plus(a, b); break;
        case '-': result = minus(a, b); break;
        // ... 其他 case
    }
    return result;
}
```

![](img/fe83c9eb79a2f981ea56556877891722_69.png)

![](img/fe83c9eb79a2f981ea56556877891722_70.png)

![](img/fe83c9eb79a2f981ea56556877891722_72.png)

![](img/fe83c9eb79a2f981ea56556877891722_73.png)

现在，我们来看使用函数指针的版本。我们定义一个函数`switch_function_pointer`，它直接接受一个函数指针作为参数：
```cpp
float switch_function_pointer(float a, float b, float (*pt2Func)(float, float)) {
    // 调用传入的函数指针
    float result = pt2Func(a, b);
    // 也可以使用更明确的语法：(*pt2Func)(a, b);
    return result;
}
```

![](img/fe83c9eb79a2f981ea56556877891722_75.png)

![](img/fe83c9eb79a2f981ea56556877891722_77.png)

![](img/fe83c9eb79a2f981ea56556877891722_78.png)

在主函数中，我们可以这样调用：
```cpp
// 使用 switch 版本
float r1 = Switch(2, 5, '+'); // 调用加法
// 使用函数指针版本
float r2 = switch_function_pointer(2, 5, &minus); // 调用减法，& 可省略
```
这个例子展示了函数指针如何使代码更简洁，并消除了`switch`语句的需要。

![](img/fe83c9eb79a2f981ea56556877891722_80.png)

![](img/fe83c9eb79a2f981ea56556877891722_81.png)

![](img/fe83c9eb79a2f981ea56556877891722_82.png)

![](img/fe83c9eb79a2f981ea56556877891722_84.png)

![](img/fe83c9eb79a2f981ea56556877891722_85.png)

![](img/fe83c9eb79a2f981ea56556877891722_86.png)

## C++中的成员函数指针 🏗️

![](img/fe83c9eb79a2f981ea56556877891722_88.png)

![](img/fe83c9eb79a2f981ea56556877891722_89.png)

![](img/fe83c9eb79a2f981ea56556877891722_90.png)

![](img/fe83c9eb79a2f981ea56556877891722_91.png)

![](img/fe83c9eb79a2f981ea56556877891722_92.png)

![](img/fe83c9eb79a2f981ea56556877891722_94.png)

C++扩展了函数指针的概念，引入了指向类成员函数的指针。这比普通的C风格函数指针更丰富。

![](img/fe83c9eb79a2f981ea56556877891722_96.png)

![](img/fe83c9eb79a2f981ea56556877891722_97.png)

![](img/fe83c9eb79a2f981ea56556877891722_99.png)

![](img/fe83c9eb79a2f981ea56556877891722_100.png)

![](img/fe83c9eb79a2f981ea56556877891722_102.png)

考虑一个简单的类`ExampleClass`：
```cpp
class ExampleClass {
private:
    int i_;
public:
    ExampleClass(int i = 0) : i_(i) {}
    // 非const成员函数
    float aFun(float a, char b, char c) { i_ += 1; return i_ + a + b + c; }
    // const成员函数
    float anotherFun(float a, char b, char c) const { return i_ + a - b + c; }
    // 静态成员函数
    static float aStaticFun(float a, char b, char c) { return a + b + c; }
};
```

![](img/fe83c9eb79a2f981ea56556877891722_104.png)

![](img/fe83c9eb79a2f981ea56556877891722_106.png)

![](img/fe83c9eb79a2f981ea56556877891722_107.png)

![](img/fe83c9eb79a2f981ea56556877891722_109.png)

![](img/fe83c9eb79a2f981ea56556877891722_111.png)

以下是定义不同类型函数指针的方法：
```cpp
// 1. 指向普通函数（或静态成员函数）的指针
float (*pt2Function)(float, char, char) = nullptr;
// 2. 指向非const成员函数的指针
float (ExampleClass::*pt2Member)(float, char, char) = nullptr;
// 3. 指向const成员函数的指针
float (ExampleClass::*pt2ConstMember)(float, char, char) const = nullptr;
```

![](img/fe83c9eb79a2f981ea56556877891722_113.png)

![](img/fe83c9eb79a2f981ea56556877891722_115.png)

![](img/fe83c9eb79a2f981ea56556877891722_116.png)

![](img/fe83c9eb79a2f981ea56556877891722_117.png)

![](img/fe83c9eb79a2f981ea56556877891722_118.png)

我们可以这样赋值和使用它们：

![](img/fe83c9eb79a2f981ea56556877891722_120.png)

![](img/fe83c9eb79a2f981ea56556877891722_122.png)


![](img/fe83c9eb79a2f981ea56556877891722_124.png)

![](img/fe83c9eb79a2f981ea56556877891722_125.png)

![](img/fe83c9eb79a2f981ea56556877891722_126.png)

![](img/fe83c9eb79a2f981ea56556877891722_127.png)

![](img/fe83c9eb79a2f981ea56556877891722_128.png)

![](img/fe83c9eb79a2f981ea56556877891722_129.png)

![](img/fe83c9eb79a2f981ea56556877891722_130.png)

![](img/fe83c9eb79a2f981ea56556877891722_131.png)

```cpp
// 为指针赋值
pt2ConstMember = &ExampleClass::anotherFun;
pt2Member = &ExampleClass::aFun;
pt2Function = &ExampleClass::aStaticFun;
// 创建对象
ExampleClass instance1(10);
// 通过对象调用成员函数指针
float result1 = (instance1.*pt2Member)(12.5, 'a', 'b');
float result2 = (instance1.*pt2ConstMember)(12.5, 'a', 'b');
// 调用普通函数指针
float result3 = pt2Function(12.5, 'a', 'b');
// 通过对象指针调用
std::unique_ptr<ExampleClass> instance2(new ExampleClass(20));
float result4 = (instance2.get()->*pt2Member)(12.5, 'a', 'b');
```
注意调用成员函数指针的特殊语法：对于对象使用`.*`，对于对象指针使用`->*`。

![](img/fe83c9eb79a2f981ea56556877891722_133.png)

## 高阶函数：传递和返回函数 🔄

![](img/fe83c9eb79a2f981ea56556877891722_135.png)

![](img/fe83c9eb79a2f981ea56556877891722_136.png)

![](img/fe83c9eb79a2f981ea56556877891722_138.png)

![](img/fe83c9eb79a2f981ea56556877891722_139.png)

函数可以作为参数传递给另一个函数（这被称为**高阶函数**），也可以作为函数的返回值。

![](img/fe83c9eb79a2f981ea56556877891722_141.png)

![](img/fe83c9eb79a2f981ea56556877891722_142.png)

![](img/fe83c9eb79a2f981ea56556877891722_143.png)

![](img/fe83c9eb79a2f981ea56556877891722_145.png)

以下是一个接收函数指针作为参数的例子：
```cpp
void passPTf(float (*pt2Func)(float, char, char)) {
    // 使用传入的函数指针
    float result = pt2Func(100, 'a', 'b');
    // ... 处理结果
}
```

![](img/fe83c9eb79a2f981ea56556877891722_146.png)

![](img/fe83c9eb79a2f981ea56556877891722_147.png)

![](img/fe83c9eb79a2f981ea56556877891722_148.png)

![](img/fe83c9eb79a2f981ea56556877891722_150.png)

![](img/fe83c9eb79a2f981ea56556877891722_151.png)

返回函数指针则更复杂，通常使用`typedef`或`using`来简化语法：

![](img/fe83c9eb79a2f981ea56556877891722_153.png)

![](img/fe83c9eb79a2f981ea56556877891722_154.png)

![](img/fe83c9eb79a2f981ea56556877891722_155.png)

![](img/fe83c9eb79a2f981ea56556877891722_156.png)

```cpp
// 使用 typedef 定义函数指针类型
typedef float (*TMyFunPtr)(float, float);
// 工厂函数，根据操作码返回对应的函数指针
TMyFunPtr getPTf(char opCode) {
    if (opCode == '+') return &plus;
    if (opCode == '-') return &minus;
    return nullptr; // 简单示例，实际应做更好处理
}
```

![](img/fe83c9eb79a2f981ea56556877891722_158.png)

![](img/fe83c9eb79a2f981ea56556877891722_159.png)

![](img/fe83c9eb79a2f981ea56556877891722_161.png)

![](img/fe83c9eb79a2f981ea56556877891722_162.png)

![](img/fe83c9eb79a2f981ea56556877891722_163.png)

在主函数中可以这样使用：

![](img/fe83c9eb79a2f981ea56556877891722_165.png)

![](img/fe83c9eb79a2f981ea56556877891722_166.png)

![](img/fe83c9eb79a2f981ea56556877891722_167.png)

![](img/fe83c9eb79a2f981ea56556877891722_169.png)

![](img/fe83c9eb79a2f981ea56556877891722_171.png)

```cpp
// 传递函数
passPTf(&aFun); // aFun 需匹配签名
// 获取并使用函数指针
TMyFunPtr pt2Func = getPTf('+');
float r1 = pt2Func(2.4, 4.2); // 加法
pt2Func = getPTf('-');
float r2 = pt2Func(4.2, 2.4); // 减法
```

![](img/fe83c9eb79a2f981ea56556877891722_173.png)

![](img/fe83c9eb79a2f981ea56556877891722_174.png)

![](img/fe83c9eb79a2f981ea56556877891722_175.png)

## 函数指针与STL仿函数的联系

![](img/fe83c9eb79a2f981ea56556877891722_177.png)

![](img/fe83c9eb79a2f981ea56556877891722_178.png)

![](img/fe83c9eb79a2f981ea56556877891722_179.png)

![](img/fe83c9eb79a2f981ea56556877891722_180.png)

![](img/fe83c9eb79a2f981ea56556877891722_182.png)

你可能会问，这与C++ STL有什么关系？函数指针是STL中仿函数（Function Objects/Functors）的前身和概念模型。然而，仿函数比普通函数指针更强大，主要体现在两点：
1.  **内联优化**：仿函数是对象，编译器可以更容易地进行内联优化，而通过地址调用的函数指针则难以内联。
2.  **状态保持**：仿函数作为对象，可以拥有内部状态（成员变量），而普通的函数指针不具备这种能力。

![](img/fe83c9eb79a2f981ea56556877891722_184.png)

![](img/fe83c9eb79a2f981ea56556877891722_185.png)

![](img/fe83c9eb79a2f981ea56556877891722_186.png)

![](img/fe83c9eb79a2f981ea56556877891722_187.png)

![](img/fe83c9eb79a2f981ea56556877891722_188.png)

![](img/fe83c9eb79a2f981ea56556877891722_189.png)

![](img/fe83c9eb79a2f981ea56556877891722_190.png)

## 总结

![](img/fe83c9eb79a2f981ea56556877891722_192.png)

本节课中我们一起学习了C++函数指针和成员函数指针的核心概念。我们了解到：
*   函数指针是存储函数地址的变量，允许运行时动态调用。
*   C++支持指向普通函数、非const成员函数、const成员函数和静态成员函数的指针，调用语法各异。
*   函数可以作为参数传递或作为返回值，构成高阶函数，提供了极大的灵活性。
*   这些概念为理解C++ STL中功能更强大的**仿函数**奠定了坚实基础。在接下来的课程中，我们将看到STL如何利用仿函数来配置算法（如排序、查找）和容器（如集合、映射的排序规则），使代码更加通用和高效。