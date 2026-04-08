# 007：链表 📚

![](img/073f1ad85e55b8db59fb2abb4644a3ce_0.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_2.png)

在本节课中，我们将要学习一种新的数据结构——链表。我们将探讨链表与数组（或向量）在性能上的差异，理解其工作原理，并动手实现单链表和双链表。通过对比，你将学会如何根据不同的应用场景选择合适的数据结构。

---

## 关于AI工具的思考 🤖

在开始学习新内容之前，我想分享一些关于使用AI编程工具的观察。最近有一项来自卡内基梅隆大学和微软的研究显示，大约62%的受访者表示在使用AI工具时减少了批判性思考。这是一个值得警惕的趋势。

正确使用AI工具的方式应该是：
*   **进行事实核查**：AI的输出可能基于有偏见或不准确的数据进行训练，需要验证其给出的答案是否真实可靠。
*   **分析和编辑输出**：不要直接复制粘贴AI生成的代码或文本。将其作为起点或头脑风暴的工具，然后进行理解和修改。
*   **让其处理繁琐工作**：利用AI自动化一些重复性任务，例如生成Getter和Setter方法，但核心逻辑仍需自己掌握。

关键在于，我们需要**更多**的批判性思维来使用这些工具，而不是更少。它们缺乏真正的智能，只是根据模式预测下一个最可能的输出。

---

## 链表的引入：为什么需要它？ 🔗

![](img/073f1ad85e55b8db59fb2abb4644a3ce_4.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_6.png)

上一节我们介绍了向量（动态数组），它虽然快速，但在某些操作上存在性能瓶颈。本节中我们来看看链表如何提供不同的性能特性。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_8.png)

向量在内存中需要一块**连续的空间**。当不断添加元素导致空间不足时，它需要分配一块更大的新内存，并将所有现有元素复制过去。这个过程是昂贵的。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_10.png)

从性能分析的角度看：
*   **平均情况**下，向`vector`末尾添加元素（`push_back`）很快，是**常数时间 O(1)**。
*   **最坏情况**下，当需要重新分配内存时，它需要复制所有`n`个元素，是**线性时间 O(n)**。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_12.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_14.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_16.png)

虽然通过几何级数扩容策略可以将平均成本“摊还”为常数时间，但偶尔的性能峰值依然存在。链表则提供了一种不同的思路。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_18.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_19.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_21.png)

---

![](img/073f1ad85e55b8db59fb2abb4644a3ce_23.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_25.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_26.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_28.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_30.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_31.png)

## 单链表：基础实现 🧱

![](img/073f1ad85e55b8db59fb2abb4644a3ce_33.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_35.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_37.png)

链表通过将数据存储在分散的“节点”中，并通过指针链接起来，避免了连续内存分配的问题。

### 核心概念：节点（Node）
链表的基本单元是节点。每个节点包含两部分：
1.  **数据（Data）**：存储的实际值。
2.  **下一个指针（Next Pointer）**：指向链表中下一个节点的内存地址。

用C++代码描述一个模板化的节点类：
```cpp
template <typename T>
class Node {
public:
    T data;          // 存储的数据
    Node<T>* next;   // 指向下一个节点的指针

    // 构造函数
    Node(T d, Node<T>* n = nullptr) : data(d), next(n) {}
};
```

### 单链表类（Singly Linked List）
链表类管理着整个节点链。它通常只需要维护一个指向第一个节点（头节点）的指针。

以下是单链表类的核心方法实现：

**1. 添加元素到前端（Push）**
此操作总是在链表头部插入新节点，速度极快。
```cpp
template <typename T>
void SinglyLinkedList<T>::push(T newData) {
    // 1. 创建新节点，其next指向原来的头节点
    Node<T>* newNode = new Node<T>(newData, first);
    // 2. 更新头指针，指向新节点
    first = newNode;
    // 3. 更新元素计数
    itemCount++;
}
```
**性能**：无论链表多长，此操作都是 **O(1)**。

**2. 查看前端元素（Peek）**
返回头节点的数据，但不移除它。
```cpp
template <typename T>
T SinglyLinkedList<T>::peek() {
    if (first == nullptr) {
        throw std::runtime_error("List is empty");
    }
    return first->data;
}
```
**性能**：**O(1)**。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_39.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_41.png)

**3. 移除前端元素（Pop）**
移除并返回头节点的数据。
```cpp
template <typename T>
T SinglyLinkedList<T>::pop() {
    if (first == nullptr) {
        throw std::runtime_error("List is empty");
    }
    T dataToReturn = first->data; // 保存要返回的数据
    Node<T>* nodeToDelete = first; // 保存要删除的节点指针
    first = first->next;          // 将头指针移动到下一个节点
    delete nodeToDelete;          // 释放原头节点的内存
    itemCount--;
    return dataToReturn;
}
```
**性能**：**O(1)**。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_43.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_45.png)

**4. 按索引获取元素（Get）**
这是链表的弱点。因为节点在内存中不连续，无法通过计算地址直接访问，必须从头开始逐个遍历。
```cpp
template <typename T>
T SinglyLinkedList<T>::get(int index) {
    if (index < 0 || index >= itemCount) {
        throw std::out_of_range("Index out of bounds");
    }
    Node<T>* currentNode = first;
    int currentIndex = 0;
    while (currentIndex < index) {
        currentNode = currentNode->next;
        currentIndex++;
    }
    return currentNode->data;
}
```
**性能**：平均和最坏情况下都是 **O(n)**。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_47.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_49.png)

### 性能对比总结：单链表 vs. 向量/数组
以下是核心操作的性能对比：

| 操作 | 单链表 | 向量/数组 | 说明 |
| :--- | :--- | :--- | :--- |
| **前端插入（Push）** | **O(1)** | O(1) 平均 / O(n) 最坏 | 链表恒定快速，向量偶尔慢。 |
| **前端移除（Pop）** | **O(1)** | O(n) | 向量移除前端元素需要移动后面所有元素。 |
| **按索引访问（Get）** | O(n) | **O(1)** | 链表的致命弱点，向量/数组的最大优势。 |
| **后端插入（Push Back）** | O(n) | **O(1)** 平均 / O(n) 最坏 | 单链表需遍历到末尾，向量通常很快。 |

![](img/073f1ad85e55b8db59fb2abb4644a3ce_51.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_52.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_54.png)

**选择策略**：
*   如果需要频繁在**任意位置插入/删除**，或者只在**前端操作**，链表是更好的选择。
*   如果需要**快速随机访问**（按索引查找），数组或向量是更好的选择。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_56.png)

---

## 双链表：更灵活的结构 🔄

上一节我们介绍了单链表，它只能高效地从一端操作。本节中我们来看看双链表如何通过在节点中增加一个指向前一个节点的指针，来实现更灵活的双端操作。

### 核心概念：双链表节点
双链表节点包含三个部分：
1.  **数据（Data）**
2.  **下一个指针（Next Pointer）**
3.  **上一个指针（Prev Pointer）**

![](img/073f1ad85e55b8db59fb2abb4644a3ce_58.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_60.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_61.png)

```cpp
template <typename T>
class DNode {
public:
    T data;
    DNode<T>* next;
    DNode<T>* prev;

    DNode(T d, DNode<T>* p = nullptr, DNode<T>* n = nullptr)
        : data(d), prev(p), next(n) {}
};
```

![](img/073f1ad85e55b8db59fb2abb4644a3ce_63.png)

### 双链表类（Doubly Linked List）
双链表类需要维护两个指针：一个指向头节点（`first`），一个指向尾节点（`last`）。这使得在两端进行操作都非常高效。

以下是双链表的一些关键方法逻辑（注意处理空链表和单个节点的边界情况）：

![](img/073f1ad85e55b8db59fb2abb4644a3ce_65.png)

**在尾部添加元素（Add Last）**
```cpp
template <typename T>
void DoublyLinkedList<T>::addLast(T newData) {
    DNode<T>* newNode = new DNode<T>(newData, last, nullptr); // 新节点的prev是原last
    if (last != nullptr) {
        last->next = newNode; // 原last的next指向新节点
    } else {
        // 如果链表为空，新节点也是第一个节点
        first = newNode;
    }
    last = newNode; // 更新尾指针
    itemCount++;
}
```

**从头部移除元素（Remove First）**
```cpp
template <typename T>
T DoublyLinkedList<T>::removeFirst() {
    if (first == nullptr) throw std::runtime_error("List is empty");
    T dataToReturn = first->data;
    DNode<T>* nodeToDelete = first;

    first = first->next; // 头指针后移
    if (first != nullptr) {
        first->prev = nullptr; // 新的头节点没有前驱
    } else {
        // 如果移除后链表为空，尾指针也要置空
        last = nullptr;
    }
    delete nodeToDelete;
    itemCount--;
    return dataToReturn;
}
```
**性能**：双链表的`addFirst`, `addLast`, `removeFirst`, `removeLast`, `peekFirst`, `peekLast` 操作都是 **O(1)**。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_67.png)

### 双链表的优势与复杂度
双链表解决了单链表只能高效从前端操作的问题，实现了双端队列（Deque）的功能。代价是每个节点需要额外的内存来存储前驱指针，并且代码逻辑因需要维护两个方向的链接而更加复杂，需要仔细处理各种边界条件（如空链表、只有一个节点等）。

---

## 总结与预告 📝

![](img/073f1ad85e55b8db59fb2abb4644a3ce_69.png)

本节课中我们一起学习了链表这种重要的数据结构。
*   我们理解了**链表**通过指针链接离散节点的工作方式，避免了向量扩容时的数据拷贝开销。
*   我们实现了**单链表**，看到它在**前端插入/删除**上具有 **O(1)** 的恒定高性能，但在**按索引访问**上是 **O(n)** 的弱点。
*   我们探讨了**双链表**，它通过增加前驱指针，允许在**两端**进行高效的 **O(1)** 操作，但增加了代码复杂度和内存开销。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_71.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_73.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_75.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_77.png)

关键收获是：**没有一种数据结构在所有场景下都是最优的**。选择数组/向量还是链表，取决于你最频繁的操作是什么。这引向了计算机科学中一个更深入的领域——算法与数据结构分析，这也是后续课程（如CS 350）的核心内容。

![](img/073f1ad85e55b8db59fb2abb4644a3ce_79.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_81.png)

![](img/073f1ad85e55b8db59fb2abb4644a3ce_83.png)

在接下来的课程中，我们将通过实验来巩固模板和链表的知识，并准备期中考试。周四我们将讲解跳棋项目的解决方案，并完成链表的收尾工作。