# 012：多线程基础与语言演进 🧵

![](img/8793dfee62c143b0ad952eb672c3ea65_1.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_3.png)

在本节课中，我们将学习C++20中的概念（Concepts）特性，并回顾C++语言的发展历程与未来展望。概念是一种强大的模板元编程工具，用于对模板参数施加约束，从而生成更清晰、更健壮的代码和更友好的错误信息。

## 概念基础 📚

![](img/8793dfee62c143b0ad952eb672c3ea65_5.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_7.png)

上一节我们介绍了课程概述，本节中我们来看看C++20概念的基本语法和用途。概念本质上是对模板参数施加要求的机制，它取代了过去的`std::enable_if`等技术，使代码意图更明确。

![](img/8793dfee62c143b0ad952eb672c3ea65_9.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_11.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_13.png)

以下是使用概念的几种基本语法形式：

![](img/8793dfee62c143b0ad952eb672c3ea65_15.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_17.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_19.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_21.png)

1.  **在模板声明后使用`requires`子句**
    ```cpp
    template <typename T>
    requires std::integral<T>
    auto add(T a, T b) { return a + b; }
    ```

![](img/8793dfee62c143b0ad952eb672c3ea65_23.png)

2.  **使用尾随`requires`子句**
    ```cpp
    template <typename T>
    auto add(T a, T b) requires std::integral<T> { return a + b; }
    ```

![](img/8793dfee62c143b0ad952eb672c3ea65_25.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_27.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_29.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_31.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_32.png)

3.  **将概念直接作为模板参数**
    ```cpp
    template <std::integral T>
    auto add(T a, T b) { return a + b; }
    ```

![](img/8793dfee62c143b0ad952eb672c3ea65_34.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_35.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_37.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_39.png)

4.  **使用受限的`auto`（缩写函数模板）**
    ```cpp
    auto add(std::integral auto a, std::integral auto b) { return a + b; }
    ```
    注意：这种形式允许`a`和`b`是不同的类型，只要它们都满足`std::integral`概念。

![](img/8793dfee62c143b0ad952eb672c3ea65_41.png)

## 概念的高级用法 ⚙️

![](img/8793dfee62c143b0ad952eb672c3ea65_43.png)

上一节我们介绍了概念的基本语法，本节中我们来看看概念更强大的功能，如重载、特化和组合。

![](img/8793dfee62c143b0ad952eb672c3ea65_45.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_47.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_49.png)

概念可以用于函数重载和模板特化，使得编译器能根据类型满足的不同概念来选择不同的实现。

![](img/8793dfee62c143b0ad952eb672c3ea65_51.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_53.png)

以下是使用概念进行函数重载的示例：

![](img/8793dfee62c143b0ad952eb672c3ea65_55.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_57.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_58.png)

```cpp
// 为前向迭代器定义
template <std::forward_iterator I>
void advance(I& iter, int n) { /* 前向移动逻辑 */ }

// 为双向迭代器定义
template <std::bidirectional_iterator I>
void advance(I& iter, int n) { /* 双向移动逻辑 */ }

![](img/8793dfee62c143b0ad952eb672c3ea65_60.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_61.png)

// 为随机访问迭代器定义
template <std::random_access_iterator I>
void advance(I& iter, int n) { iter += n; } // 直接跳转
```

![](img/8793dfee62c143b0ad952eb672c3ea65_63.png)

你还可以组合多个概念，并使用逻辑运算符。

![](img/8793dfee62c143b0ad952eb672c3ea65_65.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_67.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_69.png)

以下是组合概念的几种方式：

![](img/8793dfee62c143b0ad952eb672c3ea65_71.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_73.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_75.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_77.png)

*   **在`requires`子句中使用逻辑与**
    ```cpp
    template <typename I, typename V>
    requires std::input_iterator<I> && std::equality_comparable_with<std::iter_value_t<I>, V>
    bool find(I begin, I end, V value) { ... }
    ```
*   **使用嵌套的`requires`子句添加额外约束**
    ```cpp
    template <std::input_iterator I>
    requires requires (I iter) { { *iter } -> std::equality_comparable; }
    bool find(I begin, I end, auto value) { ... }
    ```

![](img/8793dfee62c143b0ad952eb672c3ea65_79.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_81.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_83.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_85.png)

## 定义自定义概念 🛠️

上一节我们学习了如何使用现有概念，本节中我们来看看如何定义自己的概念。你可以基于类型特征（type traits）或要求表达式（requires expressions）来创建概念。

使用`concept`关键字可以定义新概念。

以下是基于类型特征定义概念的示例：

```cpp
// 基于类型特征定义“整型”概念
template <typename T>
concept Integral = std::is_integral_v<T>;

![](img/8793dfee62c143b0ad952eb672c3ea65_87.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_89.png)

// 基于现有概念定义“有符号整型”概念
template <typename T>
concept SignedIntegral = Integral<T> && std::is_signed_v<T>;
```

更强大的是使用**要求表达式**，它可以检查类型是否支持特定的语法操作。

![](img/8793dfee62c143b0ad952eb672c3ea65_91.png)

要求表达式有几种形式：

![](img/8793dfee62c143b0ad952eb672c3ea65_93.png)

*   **简单要求**：检查表达式是否有效。
    ```cpp
    template <typename T>
    concept Addable = requires (T a, T b) {
        a + b; // 要求类型T的对象可以使用+运算符
    };
    ```
*   **类型要求**：检查嵌套类型是否存在。
    ```cpp
    template <typename T>
    concept HasValueType = requires {
        typename T::value_type; // 要求类型T有名为value_type的嵌套类型
    };
    ```
*   **复合要求**：检查表达式并对其返回类型施加约束。
    ```cpp
    template <typename T>
    concept EqualityComparable = requires (T a, T b) {
        { a == b } -> std::convertible_to<bool>; // 要求==操作的结果可转换为bool
        { a != b } -> std::convertible_to<bool>;
    };
    ```

![](img/8793dfee62c143b0ad952eb672c3ea65_95.png)

## C++标准演进与未来 🚀

上一节我们深入探讨了概念，本节中我们将视角放宽，回顾C++标准的演进历程并展望未来。了解语言的发展方向有助于我们把握现代C++编程的最佳实践。

![](img/8793dfee62c143b0ad952eb672c3ea65_97.png)

![](img/8793dfee62c143b0ad952eb672c3ea65_99.png)

C++大约每三年发布一个新标准。C++11是一次重大革新，C++14和C++17是增量更新，而C++20则引入了模块、概念、协程等重大特性。C++23是一个中型修订版，包含了一些改进和新工具。

![](img/8793dfee62c143b0ad952eb672c3ea65_101.png)

对于C++26，委员会正在规划一些重要特性。

以下是预计可能进入C++26的特性：

![](img/8793dfee62c143b0ad952eb672c3ea65_103.png)

*   **线性代数库**：提供标准的矩阵和向量运算支持。
*   **反射**：允许代码在编译时检查自身结构，简化绑定生成等任务。
*   **执行器（Executors）和网络库**：为异步和网络编程提供标准化支持。
*   **安全剖面**：响应行业对内存安全等问题的关注，定义更安全的C++子集。

## 总结与建议 📝

本节课我们一起学习了C++20的核心特性之一——概念，并回顾了C++语言的演进。概念通过为模板参数提供清晰的约束，极大地改善了泛型编程的体验，带来了更好的代码可读性和更友好的编译器错误信息。

对于想要继续提升C++技能的同学，最好的建议是动手实践。可以通过参与开源项目、完成个人玩具项目、实习或毕业设计来应用所学知识。同时，保持对C++新标准（如C++23/26）特性的关注，并利用Compiler Explorer等工具进行实验。

![](img/8793dfee62c143b0ad952eb672c3ea65_105.png)

最后，在职业发展上，保持开放心态，选择让自己有热情和成就感的方向。无论是继续深造还是进入业界，持续学习和实践都是关键。祝大家在未来的学习和职业生涯中一切顺利！