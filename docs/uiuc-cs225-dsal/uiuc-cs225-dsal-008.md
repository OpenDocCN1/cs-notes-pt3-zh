# 008：模板与链式内存 🧩

![](img/f88f79e49a671bd7e40512bec0dad7c5_1.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_3.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_5.png)

在本节课中，我们将要学习C++中的两个核心概念：**方法分派与继承**的深入规则，以及**模板**的初步介绍。我们将从理解虚函数和纯虚函数如何影响程序行为开始，然后探讨如何利用模板编写通用的、类型无关的代码。

![](img/f88f79e49a671bd7e40512bec0dad7c5_7.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_9.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_11.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_13.png)

## 方法分派与继承规则回顾 🔍

![](img/f88f79e49a671bd7e40512bec0dad7c5_15.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_17.png)

上一节我们介绍了方法分派的基本规则。本节中，我们来看看这些规则在涉及虚函数和纯虚函数时的具体应用。

![](img/f88f79e49a671bd7e40512bec0dad7c5_19.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_21.png)

当系统需要确定运行哪段代码时，会遵循以下规则：
1.  查看方法被调用对象的**类型**。
2.  检查该类型中是否存在此方法。
3.  如果存在，检查该方法是否被标记为 `virtual`（虚函数）。
4.  如果是虚函数，则检查对象的**实际运行时类型**（可能比声明的类型更具体）。
5.  使用实际运行时类型中的方法。
6.  如果未找到方法，则到其基类中查找。

![](img/f88f79e49a671bd7e40512bec0dad7c5_23.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_24.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_26.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_28.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_30.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_32.png)

以下是一个代码示例及其输出结果的总结：

```cpp
// 假设有基类 Cube 和派生类 RubiksCube
Cube c1;
c1.print1(); // 输出: Cube
c1.print2(); // 输出: Cube
c1.print3(); // 输出: Cube
c1.print4(); // 输出: Cube

![](img/f88f79e49a671bd7e40512bec0dad7c5_34.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_36.png)

RubiksCube r;
r.print1(); // 输出: RubiksCube
r.print2(); // 输出: Cube (因为 print2 非虚函数)
r.print3(); // 输出: RubiksCube
r.print4(); // 输出: RubiksCube

![](img/f88f79e49a671bd7e40512bec0dad7c5_38.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_40.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_42.png)

Cube& c_ref = r;
c_ref.print1(); // 输出: RubiksCube (虚函数，使用实际类型)
c_ref.print2(); // 输出: Cube (非虚函数，使用声明类型)
c_ref.print3(); // 输出: RubiksCube (虚函数)
c_ref.print4(); // 输出: RubiksCube (虚函数)
```

![](img/f88f79e49a671bd7e40512bec0dad7c5_44.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_45.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_47.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_49.png)

**核心区别**：`virtual` 关键字使得方法调用基于对象的**实际类型**（运行时多态），而非其声明的类型。

![](img/f88f79e49a671bd7e40512bec0dad7c5_51.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_53.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_55.png)

## 纯虚函数与抽象基类 🚫

![](img/f88f79e49a671bd7e40512bec0dad7c5_57.png)

理解了虚函数后，我们来看看一种特殊的虚函数：纯虚函数。

![](img/f88f79e49a671bd7e40512bec0dad7c5_59.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_61.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_63.png)

**纯虚函数**的语法是在声明后加上 `= 0`：
```cpp
virtual void print5() = 0;
```
这表示该函数**必须**在派生类中被实现，而在基类中没有定义。

![](img/f88f79e49a671bd7e40512bec0dad7c5_65.png)

**抽象基类**（或纯虚类）是包含至少一个纯虚函数的类。其核心规则是：
*   **抽象基类不能实例化**。尝试创建其对象会导致编译错误。
*   任何继承自抽象基类的类，**必须实现所有纯虚函数**，否则它自身也会成为抽象类。

它的作用类似于Java中的接口，但更强大，因为抽象基类可以包含数据成员和已实现的方法。

![](img/f88f79e49a671bd7e40512bec0dad7c5_67.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_69.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_71.png)

```cpp
class AbstractCube {
public:
    virtual void mustImplement() = 0; // 纯虚函数
    void concreteMethod() { /* 已实现的方法 */ }
    int someData; // 数据成员
};
// AbstractCube a; // 错误！不能实例化抽象类

![](img/f88f79e49a671bd7e40512bec0dad7c5_73.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_75.png)

class ConcreteCube : public AbstractCube {
public:
    void mustImplement() override { /* 必须提供实现 */ }
};
ConcreteCube cc; // 正确
```

![](img/f88f79e49a671bd7e40512bec0dad7c5_77.png)

## 模板简介：编写通用代码的秘诀 🧪

从方法分派转向另一个强大的C++特性：模板。当我们设计如“列表”这样的数据结构时，希望它能存储各种类型的数据（整数、字符串、对象等），但操作逻辑完全相同。

**模板**是一种让编译器为我们自动生成类型特定代码的“配方”。它允许我们将**类型作为参数**。

以下是一个简单的模板函数示例，用于返回两个值的最大值：

```cpp
// 模板声明：T 是一个类型参数
template <typename T>
T myMax(T a, T b) {
    return (a > b) ? a : b; // 三元运算符：如果 a>b 返回 a，否则返回 b
}

// 编译器会根据调用自动生成特定版本的代码
int main() {
    int i = myMax<int>(3, 5);      // 生成并调用 myMax<int>
    double d = myMax<double>(3.14, 2.99); // 生成并调用 myMax<double>
    // 通常编译器也能自动推断类型
    int j = myMax(7, 9); // 推断 T 为 int
}
```
当编译器看到 `myMax<int>(3, 5)` 时，它会将模板中的 `T` 替换为 `int`，生成一个 `int` 版本的 `myMax` 函数并编译。这发生在**编译期**，因此能进行充分的优化。

## 模板在数据结构中的应用：通用列表 📝

让我们将模板应用于之前讨论的列表抽象数据类型（ADT）。我们希望有一个能存储任何类型元素的 `List`。

以下是模板化列表的典型文件组织方式：

**list.h (接口声明)**
```cpp
#pragma once

// 声明 List 类模板
template <typename T>
class List {
public:
    List(); // 构造函数
    bool isEmpty() const;
    void insert(const T& data);
    T remove();
    // ... 其他接口函数
private:
    // 内部实现细节（例如节点指针）
    struct Node {
        T data;
        Node* next;
    };
    Node* head;
};
```

**list.hpp (模板实现)**
```cpp
// 注意：模板实现通常放在 .hpp 或直接在 .h 文件中
#include "list.h"

template <typename T>
List<T>::List() : head(nullptr) {}

template <typename T>
bool List<T>::isEmpty() const {
    return head == nullptr;
}

![](img/f88f79e49a671bd7e40512bec0dad7c5_79.png)

template <typename T>
void List<T>::insert(const T& data) {
    // 插入逻辑...
}
// ... 其他成员函数的实现
```

**main.cpp (使用列表)**
```cpp
#include "list.h"
#include "list.hpp" // 需要包含实现，因为模板是编译期展开

int main() {
    List<int> intList;       // 一个整数列表
    List<std::string> strList; // 一个字符串列表

    intList.insert(42);
    strList.insert("Hello");
    // ...
}
```
**关键点**：模板代码（`.hpp`）不是被单独编译的，而是作为一种“配方”，在编译器处理 `main.cpp` 中类似 `List<int>` 这样的代码时，被包含进来并针对具体类型 `int` 进行实例化和编译。

## 总结 🎯

![](img/f88f79e49a671bd7e40512bec0dad7c5_81.png)

![](img/f88f79e49a671bd7e40512bec0dad7c5_83.png)

本节课中我们一起学习了：
1.  **方法分派**：深入理解了 `virtual` 关键字如何实现运行时多态，以及纯虚函数（`=0`）如何定义抽象基类，强制派生类实现特定接口。
2.  **模板基础**：认识了模板作为C++强大元编程工具的基本概念。它通过在编译期将类型作为参数，允许我们编写通用、高效的代码，避免了为不同数据类型重复编写逻辑相同的代码。

![](img/f88f79e49a671bd7e40512bec0dad7c5_85.png)

模板是C++标准库（如 `vector`, `list`）的基石。掌握它，是编写现代、灵活C++程序的关键一步。在接下来的课程中，我们将利用模板来构建更复杂的数据结构。