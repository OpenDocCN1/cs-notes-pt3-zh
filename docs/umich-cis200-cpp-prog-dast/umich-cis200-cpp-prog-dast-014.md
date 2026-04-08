# 014：模板函数与模板类 📚

![](img/203e680e368e4730d31709dd3b8a58be_0.png)

在本节课中，我们将学习C++中一个强大的特性：模板。模板允许我们编写通用的、与类型无关的代码，无论是函数还是类。这为后续学习链表、栈和队列等数据结构奠定了基础。

---

## 概述 📖

模板是C++实现泛型编程的核心工具。通过模板，我们可以编写一个函数或类的框架，它能够处理多种数据类型，而无需为每种类型都重写代码。本节课将分为两部分：首先介绍模板函数，然后介绍模板类。

---

## 模板函数 ✨

![](img/203e680e368e4730d31709dd3b8a58be_2.png)

![](img/203e680e368e4730d31709dd3b8a58be_4.png)

上一节我们概述了模板的概念，本节中我们来看看如何创建和使用模板函数。模板函数允许我们定义一个函数，其参数和返回值的类型可以是通用的。

![](img/203e680e368e4730d31709dd3b8a58be_6.png)

![](img/203e680e368e4730d31709dd3b8a58be_8.png)

### 基本语法

要创建一个模板函数，需要在函数声明前使用 `template` 关键字。通常，我们使用 `typename T`（或 `class T`）来声明一个通用的类型占位符 `T`。

![](img/203e680e368e4730d31709dd3b8a58be_10.png)

```cpp
template <typename T>
void printThreeTimes(T value) {
    for (int i = 0; i < 3; ++i) {
        std::cout << value << std::endl;
    }
}
```

![](img/203e680e368e4730d31709dd3b8a58be_12.png)

在这个例子中，`T` 代表调用函数时传入的实际类型。函数 `printThreeTimes` 可以将任何具有输出流运算符（`<<`）定义的类型打印三次。

### 使用示例

![](img/203e680e368e4730d31709dd3b8a58be_14.png)

![](img/203e680e368e4730d31709dd3b8a58be_16.png)

以下是使用该模板函数的几个例子：

```cpp
printThreeTimes(10);        // T 为 int
printThreeTimes("test");    // T 为 const char*
```

![](img/203e680e368e4730d31709dd3b8a58be_18.png)

然而，如果我们尝试打印一个自定义类，而该类没有定义输出流运算符，编译器会报错。这体现了模板的编译时类型检查优势。

![](img/203e680e368e4730d31709dd3b8a58be_20.png)

![](img/203e680e368e4730d31709dd3b8a58be_22.png)

![](img/203e680e368e4730d31709dd3b8a58be_23.png)

### 为自定义类启用输出

![](img/203e680e368e4730d31709dd3b8a58be_25.png)

![](img/203e680e368e4730d31709dd3b8a58be_26.png)

为了让自定义类 `SomeClass` 能与 `printThreeTimes` 函数配合使用，我们需要为其重载输出流运算符 `<<`。

```cpp
class SomeClass {
private:
    int number;
public:
    SomeClass(int num = 0) : number(num) {}
    // 声明友元函数以访问私有成员
    friend std::ostream& operator<<(std::ostream& os, const SomeClass& obj);
};

![](img/203e680e368e4730d31709dd3b8a58be_28.png)

![](img/203e680e368e4730d31709dd3b8a58be_30.png)

// 定义输出流运算符
std::ostream& operator<<(std::ostream& os, const SomeClass& obj) {
    os << obj.number;
    return os;
}
```

定义后，就可以将 `SomeClass` 对象传递给 `printThreeTimes` 函数了。

---

## 模板类 🏗️

理解了模板函数后，我们进一步探讨模板类。模板类允许我们定义一个类，其成员变量或方法的类型是通用的。标准库中的 `vector`、`map` 等都是模板类的典型例子。

### 基本语法

![](img/203e680e368e4730d31709dd3b8a58be_32.png)

创建一个模板类与创建模板函数类似，在类定义前使用 `template` 关键字。

![](img/203e680e368e4730d31709dd3b8a58be_34.png)

```cpp
template <typename K, typename V>
class Association {
private:
    K key;
    V value;
public:
    Association(K k, V v) : key(k), value(v) {}
    K getKey() const { return key; }
    V getValue() const { return value; }
};
```

![](img/203e680e368e4730d31709dd3b8a58be_36.png)

![](img/203e680e368e4730d31709dd3b8a58be_38.png)

在这个 `Association` 类中，我们使用了两个类型参数 `K`（键）和 `V`（值），使其可以存储任意类型的键值对。

![](img/203e680e368e4730d31709dd3b8a58be_40.png)

### 使用示例

![](img/203e680e368e4730d31709dd3b8a58be_42.png)

以下是创建和使用 `Association` 模板类的例子：

```cpp
Association<std::string, std::string> dict("C++", "A programming language");
std::cout << dict.getKey() << ": " << dict.getValue() << std::endl;

Association<std::string, int> ver("C++ Version", 23);
std::cout << ver.getKey() << ": " << ver.getValue() << std::endl;
```

### 模板的灵活性

模板类可以拥有多个类型参数，并且这些类型可以不同。这提供了极大的灵活性，使我们能够构建像 `std::map` 这样强大的通用容器。

![](img/203e680e368e4730d31709dd3b8a58be_44.png)

![](img/203e680e368e4730d31709dd3b8a58be_46.png)

![](img/203e680e368e4730d31709dd3b8a58be_48.png)

---

![](img/203e680e368e4730d31709dd3b8a58be_50.png)

![](img/203e680e368e4730d31709dd3b8a58be_52.png)

## 核心概念与注意事项 ⚠️

在使用模板时，有几个核心概念和注意事项需要牢记：

1.  **编译时实例化**：模板代码在编译时根据具体使用的类型生成对应的代码。这被称为“模板实例化”。
2.  **类型要求**：模板函数或类中对类型 `T` 的操作（如比较、输出）必须对该类型有效。如果 `T` 不支持某个操作，代码将无法编译。
3.  **代码膨胀**：为多种类型实例化模板可能会导致生成的可执行文件体积增大。
4.  **分离编译问题**：模板的定义通常需要放在头文件（`.h` 或 `.hpp`）中，因为编译器需要在编译时看到完整的定义来实例化它们。

![](img/203e680e368e4730d31709dd3b8a58be_54.png)

---

![](img/203e680e368e4730d31709dd3b8a58be_56.png)

## 总结 🎯

![](img/203e680e368e4730d31709dd3b8a58be_58.png)

本节课中我们一起学习了C++模板的核心知识。

![](img/203e680e368e4730d31709dd3b8a58be_60.png)

*   **模板函数**：让我们能够编写处理通用类型的函数，提高了代码的复用性。
*   **模板类**：允许我们创建可以存储或操作多种数据类型的类，是构建通用数据结构（如链表、栈）的基础。
*   **核心机制**：模板依赖于编译时多态和类型检查，确保了类型安全的同时，也要求所使用的类型满足特定的操作接口。

![](img/203e680e368e4730d31709dd3b8a58be_62.png)

掌握模板是深入理解C++标准库和实现自定义高级数据结构的关键一步。在接下来的课程中，我们将运用模板知识来构建我们自己的链表。