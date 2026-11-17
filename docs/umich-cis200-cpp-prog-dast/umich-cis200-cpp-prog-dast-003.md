# 003：容器 🗂️


![](img/8fb9df090e5ffdebf34e4c6d6713e012_3.png)



![](img/8fb9df090e5ffdebf34e4c6d6713e012_9.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_11.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_12.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_14.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_16.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_18.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_20.png)

在本节课中，我们将要学习C++标准模板库（STL）中的容器。容器是用于存储和组织数据的数据结构。我们将了解不同类型的容器及其基本操作，为后续学习更复杂的数据结构打下基础。

![](img/8fb9df090e5ffdebf34e4c6d6713e012_22.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_24.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_26.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_28.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_30.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_32.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_34.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_35.png)

## 项目回顾与容器介绍

![](img/8fb9df090e5ffdebf34e4c6d6713e012_37.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_39.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_41.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_43.png)

上一节我们介绍了项目一的实现，本节中我们来看看C++标准库中提供的各种容器。容器是预定义的数据结构，可以帮助我们更高效地管理数据。

![](img/8fb9df090e5ffdebf34e4c6d6713e012_45.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_47.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_49.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_51.png)

C++标准库提供了多种容器类型，每种都有其特定的用途和性能特征。

## 标准模板库（STL）容器概览

![](img/8fb9df090e5ffdebf34e4c6d6713e012_53.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_54.png)

STL容器是模板类，这意味着它们可以存储任何类型的数据。最常用的容器是`vector`，我们之前已经使用过。

![](img/8fb9df090e5ffdebf34e4c6d6713e012_56.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_58.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_60.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_62.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_64.png)

除了`vector`，还有其他有用的容器：

![](img/8fb9df090e5ffdebf34e4c6d6713e012_66.png)

*   **`list`**: 一个双向链表。对于在序列中间频繁插入或删除元素的操作很高效。
*   **`pair`**: 用于将两个值组合成一个单一单元。例如，`pair<string, int>`可以将一个字符串和一个整数关联起来。
*   **`map`**: 一种关联容器，存储键值对，其中每个键都是唯一的。可以像字典一样根据键快速查找值。
*   **`set`**: 存储唯一值的集合。自动确保没有重复元素。
*   **`queue`**: 队列，遵循先进先出（FIFO）原则。
*   **`deque`**: 双端队列，允许在头部和尾部高效地插入和删除元素。

## 容器通用操作与算法

![](img/8fb9df090e5ffdebf34e4c6d6713e012_68.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_70.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_72.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_73.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_75.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_77.png)

许多容器支持类似的操作，例如使用迭代器进行遍历。此外，STL还提供了一系列通用算法，可以应用于这些容器。

以下是几个有用的通用算法：

![](img/8fb9df090e5ffdebf34e4c6d6713e012_79.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_81.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_83.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_85.png)

*   **`find`**: 在给定范围内查找特定值。
    ```cpp
    auto it = find(container.begin(), container.end(), valueToFind);
    ```
*   **`sort`**: 对容器中的元素进行排序。默认使用 `<` 运算符进行比较。
    ```cpp
    sort(container.begin(), container.end());
    ```
    对于自定义类，可以通过重载 `<` 运算符来定义排序规则。

![](img/8fb9df090e5ffdebf34e4c6d6713e012_87.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_89.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_91.png)

![](img/8fb9df090e5ffdebf34e4c6d6713e012_92.png)

## 选择正确的容器

选择哪种容器取决于你的具体需求：
*   需要随机访问元素？使用 `vector` 或 `deque`。
*   需要在中间频繁插入/删除？使用 `list`。
*   需要根据键快速查找？使用 `map`。
*   需要确保元素唯一性？使用 `set`。
*   需要先进先出的顺序？使用 `queue`。

![](img/8fb9df090e5ffdebf34e4c6d6713e012_94.png)





![](img/8fb9df090e5ffdebf34e4c6d6713e012_103.png)



理解每种容器的优缺点对于编写高效的程序至关重要。

## 总结

![](img/8fb9df090e5ffdebf34e4c6d6713e012_108.png)

本节课中我们一起学习了C++标准模板库中的多种容器，包括`list`、`pair`、`map`、`set`、`queue`和`deque`。我们了解了它们的基本概念、通用操作（如`find`和`sort`）以及如何根据不同的应用场景选择合适的容器。掌握这些工具将极大地提升我们管理和操作数据的能力。