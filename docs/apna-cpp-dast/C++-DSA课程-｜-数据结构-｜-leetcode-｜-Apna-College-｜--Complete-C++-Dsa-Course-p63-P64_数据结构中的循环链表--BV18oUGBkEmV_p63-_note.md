# C++ 数据结构课程：P63-P64：循环链表 🔄

![](img/b5f436c441324955190f79dbbfb7ee56_0.png)

在本节课中，我们将详细学习循环链表的概念。循环链表是链表的一种变体，其最后一个节点的指针指向头节点，形成一个环。我们将从零开始实现循环链表，并学习如何插入、删除节点以及遍历链表。

---

## 循环链表的基本概念

上一节我们介绍了普通链表，本节中我们来看看循环链表。循环链表与普通单链表的主要区别在于其尾节点的指针指向头节点，而不是 `null`。这使得链表形成一个闭环。

在普通单链表中，我们有一个头指针和一个尾指针，尾指针的 `next` 指向 `null`。而在循环链表中，尾节点的 `next` 指针指向头节点。这意味着我们可以从链表的任何节点出发，最终都能回到起点。

循环链表的基本结构可以用以下伪代码表示：
```cpp
class Node {
public:
    int data;
    Node* next;
    Node(int val) {
        data = val;
        next = nullptr;
    }
};

class CircularLinkedList {
private:
    Node* head;
    Node* tail;
public:
    CircularLinkedList() {
        head = nullptr;
        tail = nullptr;
    }
    // ... 其他成员函数
};
```

---

## 实现节点和链表类

首先，我们需要创建节点类和循环链表类。以下是实现步骤：

以下是节点类的定义：
```cpp
class Node {
public:
    int data;
    Node* next;
    Node(int val) {
        data = val;
        next = nullptr;
    }
};
```

接下来是循环链表类的框架：
```cpp
class CircularLinkedList {
private:
    Node* head;
    Node* tail;
public:
    CircularLinkedList() {
        head = nullptr;
        tail = nullptr;
    }
    // 后续将在这里添加成员函数
};
```

---

## 在头部插入节点

现在，我们来实现第一个操作：在循环链表的头部插入一个新节点。需要考虑链表为空和非空两种情况。

以下是插入操作的逻辑步骤：
1.  创建一个新节点。
2.  如果链表为空（`head == nullptr`），则新节点既是头节点也是尾节点，并且其 `next` 指针指向自身。
3.  如果链表不为空，则将新节点的 `next` 指向当前头节点，更新尾节点的 `next` 指向新节点，最后将头指针更新为新节点。

对应的代码实现如下：
```cpp
void insertAtHead(int val) {
    Node* newNode = new Node(val);
    if (head == nullptr) {
        head = newNode;
        tail = newNode;
        newNode->next = head; // 指向自身形成环
    } else {
        newNode->next = head;
        tail->next = newNode;
        head = newNode;
    }
}
```

---

## 遍历并打印链表

为了验证我们的插入操作，我们需要一个能打印链表所有元素的函数。由于链表是循环的，遍历的终止条件不再是 `nullptr`，而是回到头节点。

以下是打印链表的步骤：
1.  如果链表为空，直接返回。
2.  从头节点开始，打印当前节点的数据。
3.  使用一个临时指针移动到下一个节点。
4.  循环继续，直到临时指针再次回到头节点。

对应的代码实现如下：
```cpp
void printList() {
    if (head == nullptr) {
        return;
    }
    Node* temp = head;
    do {
        std::cout << temp->data << " -> ";
        temp = temp->next;
    } while (temp != head);
    std::cout << "(head)" << std::endl; // 指示回到头部
}
```

---

## 在尾部插入节点

接下来，我们实现在循环链表尾部插入节点的功能。其逻辑与头部插入类似。

以下是插入尾部的逻辑步骤：
1.  创建一个新节点。
2.  如果链表为空，处理方式与头部插入相同。
3.  如果链表不为空，则将新节点的 `next` 指向头节点，将当前尾节点的 `next` 指向新节点，最后更新尾指针为新节点。

对应的代码实现如下：
```cpp
void insertAtTail(int val) {
    Node* newNode = new Node(val);
    if (head == nullptr) {
        head = newNode;
        tail = newNode;
        newNode->next = head;
    } else {
        newNode->next = head;
        tail->next = newNode;
        tail = newNode;
    }
}
```

---

## 删除头节点

现在，我们学习如何删除循环链表的头节点。我们需要处理三种情况：链表为空、只有一个节点、有多个节点。

以下是删除头节点的逻辑步骤：
1.  **链表为空**：无节点可删，直接返回。
2.  **只有一个节点**：删除该节点，并将 `head` 和 `tail` 都设为 `nullptr`。
3.  **有多个节点**：将头指针移动到下一个节点，更新尾节点的 `next` 指针指向新的头节点，然后删除原头节点。

对应的代码实现如下：
```cpp
void deleteAtHead() {
    if (head == nullptr) {
        return; // 情况1：空链表
    }
    if (head == tail) {
        delete head; // 情况2：只有一个节点
        head = nullptr;
        tail = nullptr;
    } else {
        Node* temp = head; // 情况3：多个节点
        head = head->next;
        tail->next = head;
        delete temp;
    }
}
```

---

## 删除尾节点

最后，我们实现删除循环链表尾节点的操作。这同样需要处理空链表、单节点链表和多节点链表的情况。

以下是删除尾节点的逻辑步骤：
1.  **链表为空**：直接返回。
2.  **只有一个节点**：与删除头节点处理方式相同。
3.  **有多个节点**：遍历链表找到尾节点的前一个节点（`prev`）。将 `prev` 的 `next` 指向头节点，更新尾指针为 `prev`，然后删除原尾节点。

对应的代码实现如下：
```cpp
void deleteAtTail() {
    if (head == nullptr) {
        return; // 情况1：空链表
    }
    if (head == tail) {
        delete head; // 情况2：只有一个节点
        head = nullptr;
        tail = nullptr;
    } else {
        Node* temp = tail; // 情况3：多个节点
        Node* prev = head;
        while (prev->next != tail) {
            prev = prev->next;
        }
        prev->next = head; // prev成为新的尾节点，指向头
        tail = prev;
        delete temp;
    }
}
```

---

![](img/b5f436c441324955190f79dbbfb7ee56_2.png)

本节课中我们一起学习了循环链表的核心概念和基本操作。我们实现了循环链表的类结构，并完成了在头部和尾部插入节点、遍历链表、以及删除头和尾节点的功能。循环链表因其闭环特性，在某些场景（如轮询调度）中非常有用。理解这些基础操作是解决更复杂链表问题的重要一步。