# 017：函数指针和成员函数指针 🧭



在本节课中，我们将要学习C++中的函数指针和成员函数指针。这些概念是理解C++标准模板库（STL）中**函数对象**（或称仿函数）的基础。函数指针允许我们将函数作为数据来处理，为算法和容器的灵活配置提供了可能。





## 概述：函数指针与策略模式


函数指针是C++ STL中仿函数功能的概念基础。仿函数本质上应用了**策略模式**，使得我们能够在不改变算法或容器内部实现细节的情况下，指导和修改它们的行为。











上一节我们介绍了课程背景，本节中我们来看看函数指针的具体概念。





## 什么是函数指针？ 🎯





顾名思义，函数指针是一个指针变量，它存储了函数的地址。



程序运行时，包含数据和代码。函数是代码空间的一部分。我们可以通过函数的名称（标签）获取其地址，并将其存储起来。这样，我们就不必在源代码中硬编码调用哪个函数，而是在运行时动态决定。







函数指针在C语言中就已存在，并延续到C++中。它们有多种用途，例如：
*   作为`qsort`等函数的比较回调函数。
*   用于线程库（如Pthreads）或窗口系统中的回调函数和定时器。
*   C++编译器使用函数指针表来实现虚函数的分发机制。



## 基础函数指针示例






让我们通过一个简单的例子来理解函数指针。首先，我们看一个不使用函数指针的版本。





我们定义了四个基础的算术运算函数：
```cpp
float plus(float a, float b) { return a + b; }
float minus(float a, float b) { return a - b; }
float multiply(float a, float b) { return a * b; }
float divide(float a, float b) { return a / b; }
```







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





现在，我们来看使用函数指针的版本。我们定义一个函数`switch_function_pointer`，它直接接受一个函数指针作为参数：
```cpp
float switch_function_pointer(float a, float b, float (*pt2Func)(float, float)) {
    // 调用传入的函数指针
    float result = pt2Func(a, b);
    // 也可以使用更明确的语法：(*pt2Func)(a, b);
    return result;
}
```




在主函数中，我们可以这样调用：
```cpp
// 使用 switch 版本
float r1 = Switch(2, 5, '+'); // 调用加法
// 使用函数指针版本
float r2 = switch_function_pointer(2, 5, &minus); // 调用减法，& 可省略
```
这个例子展示了函数指针如何使代码更简洁，并消除了`switch`语句的需要。







## C++中的成员函数指针 🏗️







C++扩展了函数指针的概念，引入了指向类成员函数的指针。这比普通的C风格函数指针更丰富。






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






以下是定义不同类型函数指针的方法：
```cpp
// 1. 指向普通函数（或静态成员函数）的指针
float (*pt2Function)(float, char, char) = nullptr;
// 2. 指向非const成员函数的指针
float (ExampleClass::*pt2Member)(float, char, char) = nullptr;
// 3. 指向const成员函数的指针
float (ExampleClass::*pt2ConstMember)(float, char, char) const = nullptr;
```






我们可以这样赋值和使用它们：












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


## 高阶函数：传递和返回函数 🔄





函数可以作为参数传递给另一个函数（这被称为**高阶函数**），也可以作为函数的返回值。





以下是一个接收函数指针作为参数的例子：
```cpp
void passPTf(float (*pt2Func)(float, char, char)) {
    // 使用传入的函数指针
    float result = pt2Func(100, 'a', 'b');
    // ... 处理结果
}
```






返回函数指针则更复杂，通常使用`typedef`或`using`来简化语法：





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






在主函数中可以这样使用：






```cpp
// 传递函数
passPTf(&aFun); // aFun 需匹配签名
// 获取并使用函数指针
TMyFunPtr pt2Func = getPTf('+');
float r1 = pt2Func(2.4, 4.2); // 加法
pt2Func = getPTf('-');
float r2 = pt2Func(4.2, 2.4); // 减法
```




## 函数指针与STL仿函数的联系






你可能会问，这与C++ STL有什么关系？函数指针是STL中仿函数（Function Objects/Functors）的前身和概念模型。然而，仿函数比普通函数指针更强大，主要体现在两点：
1.  **内联优化**：仿函数是对象，编译器可以更容易地进行内联优化，而通过地址调用的函数指针则难以内联。
2.  **状态保持**：仿函数作为对象，可以拥有内部状态（成员变量），而普通的函数指针不具备这种能力。








## 总结

![](img/fe83c9eb79a2f981ea56556877891722_192.png)

本节课中我们一起学习了C++函数指针和成员函数指针的核心概念。我们了解到：
*   函数指针是存储函数地址的变量，允许运行时动态调用。
*   C++支持指向普通函数、非const成员函数、const成员函数和静态成员函数的指针，调用语法各异。
*   函数可以作为参数传递或作为返回值，构成高阶函数，提供了极大的灵活性。
*   这些概念为理解C++ STL中功能更强大的**仿函数**奠定了坚实基础。在接下来的课程中，我们将看到STL如何利用仿函数来配置算法（如排序、查找）和容器（如集合、映射的排序规则），使代码更加通用和高效。