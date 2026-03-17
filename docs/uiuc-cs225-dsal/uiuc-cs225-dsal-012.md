# 012：迭代器与树的入门

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_1.png)

在本节课中，我们将要学习两个核心概念：**迭代器**和**树**。迭代器是C++中一个非常重要的概念，它为我们提供了一种统一的方式来访问和遍历各种数据结构中的元素，而无需关心其内部实现细节。之后，我们将初步了解树这种数据结构。

## 迭代器是什么？🤔

上一节我们介绍了课程的主要内容。本节中，我们来看看迭代器的基本概念。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_3.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_4.png)

迭代器是C++中一个非常重要的概念，它帮助我们访问数据集。假设我们想要遍历数据结构中的每一个元素，例如一个数组、一个链表或一个超立方体。我们如何访问所有这些元素？我们希望逐个地、按某种顺序访问它们。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_6.png)

让我们思考如何实现这一点。迭代器的理念是提供一个统一的接口，让你能够完成这样的操作。这样，你就不需要知道访问不同数据结构的不同方法。否则，例如，在链表中如何定位元素？我们有一个链表节点指针作为数据，我们称它为`cur`。要访问数据，我们使用`cur->data`。在数组中，我们使用索引，如`data[index]`。在超立方体中，访问方式可能更复杂，例如`data[x][y][z]`。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_8.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_10.png)

以下是访问不同数据结构“下一个”元素的方法：
*   **链表**：`cur = cur->next;`
*   **数组**：`index++;`
*   **超立方体**：方式复杂且不直观。

迭代器的作用是，无论底层数据结构是什么，都使用相同的接口来遍历其中的所有数据。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_12.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_14.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_16.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_18.png)

## 迭代器接口的要求 📋

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_20.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_22.png)

上一节我们了解了迭代器的目的。本节中我们来看看实现迭代器接口的具体要求。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_24.png)

一个提供迭代器接口的类必须提供两个函数。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_26.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_28.png)

在类中，如果我编写了`Hypercube`类并希望允许你使用迭代器访问它，我需要提供两个函数：
1.  `iterator begin()`：返回指向数据结构中**第一个元素**的迭代器。
2.  `iterator end()`：返回指向数据结构**末尾之后一个位置**的迭代器。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_30.png)

每个数据结构都必须有自己的迭代器，因为它封装了在该数据结构中移动的方式。

让我们理解“末尾之后一个位置”的含义。对于一个数组，`begin()`指向起始位置，`end()`指向最后一个元素之后的位置。对于一个链表，`begin()`指向头节点，`end()`则指向`nullptr`。`end()`是我们知道何时终止循环的方式，类似于标准`for`循环中的终止条件。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_32.png)

一个典型的基于迭代器的循环如下所示：
```cpp
for (auto it = data_structure.begin(); it != data_structure.end(); ++it) {
    // 使用 *it 访问当前元素
}
```

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_34.png)

## 迭代器类需要实现什么？🔧

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_36.png)

上一节我们介绍了数据结构需要提供的接口。本节中我们来看看迭代器类本身需要实现哪些操作。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_38.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_40.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_42.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_43.png)

迭代器类需要实现三个核心操作：
1.  **前置递增运算符 (`++it`)**：移动到下一个元素，并返回递增后的迭代器。
2.  **不等运算符 (`it1 != it2`)**：比较两个迭代器是否不相等。
3.  **解引用运算符 (`*it`)**：返回迭代器当前指向的数据。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_45.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_47.png)

**前置递增**意味着先增加再返回值。与之相对的是**后置递增** (`it++`)，它先保存原值，递增后返回保存的原值。在迭代器上下文中，通常使用前置递增效率更高。

只有这三个操作是必须实现的。实现了这些，就拥有了一个可用的迭代器接口。

## 如何实现迭代器？💻

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_49.png)

上一节我们列出了迭代器类的必需操作。本节中我们通过一个链表迭代器的例子，看看如何具体实现。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_51.png)

让我们尝试为链表编写迭代器接口。首先，数据结构（如`MyLinkedList`）需要提供`begin()`和`end()`函数。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_53.png)

`begin()`函数可能如下实现：
```cpp
iterator begin() { return iterator(head); } // 假设head是链表头指针
```
`end()`函数可能如下实现：
```cpp
iterator end() { return iterator(nullptr); }
```

迭代器类本身需要一个构造函数来初始化其内部状态（例如一个节点指针）。它的构造函数可能像这样：
```cpp
class iterator {
private:
    ListNode* ptr;
public:
    iterator(ListNode* p) : ptr(p) {} // 构造函数
    // ... 其他必需的操作（++, !=, *）
};
```

对于数组，`begin()`可能返回指向索引0的迭代器，`end()`返回指向索引`size`（即数组长度）的迭代器。

## 迭代器的使用示例 🦒

上一节我们探讨了如何实现迭代器。本节中我们来看看如何在代码中使用迭代器。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_55.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_57.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_59.png)

首先，我们定义一个简单的`Animal`类，并创建一个包含动物的`vector`（一种动态数组）。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_61.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_63.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_65.png)

最详细的使用迭代器的方式如下：
```cpp
for (std::vector<Animal>::iterator it = zoo.begin(); it != zoo.end(); it++) {
    std::cout << it->name << " eats " << it->food << std::endl;
}
```
这里，`it++`是后置递增。使用`*it`可以访问元素，对于具有成员的结构，也可以使用`it->`。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_67.png)

为了使代码更简洁，可以使用`auto`关键字：
```cpp
for (auto it = zoo.begin(); it != zoo.end(); ++it) {
    std::cout << it->name << " eats " << it->food << std::endl;
}
```

最简洁的方式是使用**基于范围的for循环**：
```cpp
for (const auto& animal : zoo) {
    std::cout << animal.name << " eats " << animal.food << std::endl;
}
```
编译器会将这种语法转换为使用迭代器的形式。标准模板库（STL）中的容器（如`vector`, `list`, `unordered_set`）都实现了迭代器接口，因此都可以用这种方式遍历。

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_69.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_71.png)

## 总结 📚

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_73.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_74.png)

![](img/b4cf9a1c2b17995ab8a9b3e8f6e37cf0_76.png)

本节课中我们一起学习了迭代器的核心概念。迭代器提供了一种统一的机制来遍历各种数据结构，隐藏了底层实现的复杂性。我们了解到，一个支持迭代器的数据结构需要提供`begin()`和`end()`方法，而迭代器类型本身需要实现前置递增(`++it`)、不等比较(`!=`)和解引用(`*`)操作。通过使用`auto`关键字和基于范围的for循环，我们可以写出非常简洁和清晰的遍历代码。掌握迭代器是有效使用C++标准库和许多自定义数据结构的关键。