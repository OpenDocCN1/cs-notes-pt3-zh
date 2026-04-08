# 006：栈与队列 🧱🚶‍♂️

![](img/b2126b3ac604e611deb65ec0b95636fa_1.png)

在本节课中，我们将要学习两种重要的数据结构：栈（Stack）和队列（Queue）。我们将了解它们的基本概念、操作、实现方式以及性能特点。通过对比不同的实现方法，你将理解如何根据具体需求选择合适的数据结构。

![](img/b2126b3ac604e611deb65ec0b95636fa_3.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_5.png)

---

## 栈（Stack）📚

栈是一种遵循**后进先出**（LIFO, Last In First Out）原则的数据结构。这意味着你只能从栈的顶部添加或移除元素。栈的操作非常有限，但正是这种限制使其在许多场景下非常有用，例如函数调用栈。

### 栈的核心操作

以下是栈通常支持的几个核心操作：

*   **`push(item)`**: 将一个元素添加到栈的顶部。
*   **`pop()`**: 移除并返回栈顶的元素。
*   **`peek()` 或 `top()`**: 返回栈顶的元素但不移除它。
*   **`isEmpty()`**: 检查栈是否为空。

![](img/b2126b3ac604e611deb65ec0b95636fa_7.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_8.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_10.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_12.png)

### 栈的简单实现

我们可以使用C++的 `vector` 作为底层存储来轻松实现一个栈。这样做的好处是可以利用 `vector` 已经优化过的内存管理。

```cpp
template <typename T>
class Stack {
private:
    std::vector<T> items; // 使用vector作为底层存储

public:
    Stack() {} // 构造函数

    void push(const T& item) {
        items.push_back(item); // 添加到末尾
    }

    T pop() {
        if (isEmpty()) {
            throw std::invalid_argument("Stack is empty");
        }
        T item = items.back(); // 获取最后一个元素
        items.pop_back();      // 移除最后一个元素
        return item;
    }

    T peek() const {
        if (isEmpty()) {
            throw std::invalid_argument("Stack is empty");
        }
        return items.back(); // 返回最后一个元素
    }

    bool isEmpty() const {
        return items.size() == 0;
    }
};
```

![](img/b2126b3ac604e611deb65ec0b95636fa_14.png)

### 栈的性能分析

![](img/b2126b3ac604e611deb65ec0b95636fa_16.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_18.png)

上一节我们介绍了栈的基本实现，本节中我们来看看它的时间复杂度，这对于理解其效率至关重要。

*   **`push` 操作**: 平均时间复杂度为 **O(1)**。虽然 `vector` 偶尔需要扩容（时间复杂度 O(n)），但通过**摊还分析**，其平均成本是常数级的。
*   **`pop` 操作**: 平均时间复杂度为 **O(1)**。移除末尾元素通常很快，虽然 `vector` 也可能在元素过少时收缩内存，但平均来看仍是常数时间。
*   **`peek` 和 `isEmpty` 操作**: 时间复杂度为 **O(1)**。这些操作只涉及访问已知位置或检查大小。

---

![](img/b2126b3ac604e611deb65ec0b95636fa_20.png)

## 队列（Queue）🔄

队列是一种遵循**先进先出**（FIFO, First In First Out）原则的数据结构。这就像现实生活中的排队，最先加入的人最先得到服务。队列在任务调度、消息传递等场景中非常常见。

### 队列的核心操作

![](img/b2126b3ac604e611deb65ec0b95636fa_22.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_24.png)

以下是队列通常支持的几个核心操作：

*   **`enqueue(item)`**: 将一个元素添加到队列的末尾。
*   **`dequeue()`**: 移除并返回队列前端的元素。
*   **`front()`**: 返回队列前端的元素但不移除它。
*   **`isEmpty()`**: 检查队列是否为空。

### 队列的实现方式

![](img/b2126b3ac604e611deb65ec0b95636fa_26.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_28.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_30.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_32.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_34.png)

使用 `vector` 直接实现队列的 `dequeue` 操作（移除前端元素）效率很低，因为需要将所有后续元素向前移动，时间复杂度为 O(n)。因此，我们需要更聪明的方法。

![](img/b2126b3ac604e611deb65ec0b95636fa_36.png)

#### 方法一：简单但低效的实现

这种方法直观但性能差，因为它每次出队都要移动大量元素。

```cpp
template <typename T>
class SlowQueue {
private:
    std::vector<T> items;

public:
    void enqueue(const T& item) {
        items.push_back(item); // O(1) 平均
    }

    T dequeue() {
        if (isEmpty()) throw std::invalid_argument("Queue is empty");
        T item = items.front(); // 获取第一个元素
        items.erase(items.begin()); // 移除第一个元素，O(n)
        return item;
    }
    // ... 其他方法
};
```

#### 方法二：使用索引标记的“更快”队列

![](img/b2126b3ac604e611deb65ec0b95636fa_38.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_40.png)

为了改进性能，我们可以不实际删除前端元素，而是用一个索引 `frontIndex` 来标记队列头部的位置。这样 `dequeue` 操作就变成了 O(1)。

![](img/b2126b3ac604e611deb65ec0b95636fa_42.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_44.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_46.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_48.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_50.png)

```cpp
template <typename T>
class FasterQueue {
private:
    std::vector<T> items;
    int frontIndex;
    int itemCount;

![](img/b2126b3ac604e611deb65ec0b95636fa_52.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_54.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_56.png)

public:
    FasterQueue() : frontIndex(0), itemCount(0) {
        items.resize(10); // 预分配一些空间
    }

    void enqueue(const T& item) {
        // 需要检查并处理扩容
        if (itemCount >= items.size()) {
            // 扩容逻辑...
        }
        int backIndex = (frontIndex + itemCount) % items.size();
        items[backIndex] = item;
        itemCount++;
    }

    T dequeue() {
        if (isEmpty()) throw std::invalid_argument("Queue is empty");
        T item = items[frontIndex];
        frontIndex = (frontIndex + 1) % items.size(); // 循环利用空间
        itemCount--;
        return item;
    }
    // ... 其他方法
};
```
这种方法创建了一个**循环队列**。当尾部到达数组末尾时，它会绕回到开头使用之前已出队元素空出的空间。虽然偶尔仍需扩容，但 `enqueue` 和 `dequeue` 操作的平均时间复杂度都达到了 O(1)。

#### 方法三：使用链表的实现

![](img/b2126b3ac604e611deb65ec0b95636fa_58.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_60.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_62.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_64.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_66.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_68.png)

最优雅且性能稳定的实现方式是使用**链表**。链表允许我们在常数时间内向头部或尾部添加/删除节点，完全避免了数组扩容和元素移动的问题。

![](img/b2126b3ac604e611deb65ec0b95636fa_70.png)

```cpp
template <typename T>
class LinkedQueue {
private:
    struct Node {
        T data;
        Node* next;
        Node(const T& d, Node* n = nullptr) : data(d), next(n) {}
    };
    Node* frontNode;
    Node* backNode;
    int count;

![](img/b2126b3ac604e611deb65ec0b95636fa_72.png)

public:
    LinkedQueue() : frontNode(nullptr), backNode(nullptr), count(0) {}

    void enqueue(const T& item) {
        Node* newNode = new Node(item);
        if (isEmpty()) {
            frontNode = backNode = newNode;
        } else {
            backNode->next = newNode;
            backNode = newNode;
        }
        count++;
    }

    T dequeue() {
        if (isEmpty()) throw std::invalid_argument("Queue is empty");
        T item = frontNode->data;
        Node* temp = frontNode;
        frontNode = frontNode->next;
        delete temp;
        count--;
        if (frontNode == nullptr) backNode = nullptr; // 队列变空
        return item;
    }
    // ... 其他方法
};
```
链表实现的队列，其 `enqueue` 和 `dequeue` 操作的时间复杂度始终是 **O(1)**，是最理想的队列实现方式之一。

---

## 总结 🎯

本节课中我们一起学习了栈和队列这两种基础且重要的数据结构。

![](img/b2126b3ac604e611deb65ec0b95636fa_74.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_76.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_78.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_80.png)

*   **栈** 是一种LIFO结构，核心操作是 `push`、`pop` 和 `peek`。我们使用 `vector` 可以轻松实现一个高效的栈。
*   **队列** 是一种FIFO结构，核心操作是 `enqueue`、`dequeue` 和 `front`。直接使用 `vector` 实现出队操作效率低下。
*   我们探讨了三种队列实现：低效的简单实现、高效的循环数组实现以及最优的链表实现。**链表实现**在时间复杂度和灵活性上通常是最佳选择。
*   理解这些数据结构的**抽象**（即它们提供什么操作）与**具体实现**（即如何实现这些操作以保障性能）之间的区别至关重要。作为使用者，你关心接口；作为设计者，你关心如何实现高效的接口。

![](img/b2126b3ac604e611deb65ec0b95636fa_82.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_84.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_86.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_87.png)

![](img/b2126b3ac604e611deb65ec0b95636fa_89.png)

掌握栈和队列将为你学习更复杂的算法（如深度优先搜索使用栈，广度优先搜索使用队列）打下坚实的基础。