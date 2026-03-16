# 加州大学C语言结构化程序设计：P17：二叉树代码详解

![](img/7c8ee3c98eaa3d85f6264138f036793b_1.png)

## 概述
在本节课中，我们将学习一种非常重要的数据结构——二叉树。我们将通过详细的C语言代码，了解如何定义二叉树节点、如何遍历二叉树，以及如何从数组数据递归地构建一棵二叉树。本课程内容面向希望深入学习计算机科学或C++序列的同学，其中会大量运用递归和指针的概念。

---

## 二叉树节点定义与类型别名

上一节我们介绍了二叉树的重要性，本节中我们来看看如何在C语言中定义它的基本结构。

为了简化代码并提高可读性，我们使用 `typedef` 来创建类型别名。首先，我们定义一个字符类型作为节点存储的数据。在实际应用中，数据可以很复杂，但在这个简单的例子中，我们只在节点中存储一个字符。

```c
typedef char DataType;
```

接下来，我们定义二叉树节点的结构。它类似于链表节点，但关键区别在于每个节点包含**两个指针**，分别指向左子树和右子树。

```c
struct node {
    DataType data;
    struct node *left;
    struct node *right;
};
```

为了使代码更简洁，我们为这个结构体及其指针创建类型别名。

```c
typedef struct node Node;
typedef Node* BTree;
```

这里，`BTree` 被定义为一个指向 `Node` 的指针。在C语言中，我们通常用一个指向树根节点的指针来代表整棵二叉树。

---

## 二叉树的遍历：中序遍历

定义了树的结构后，我们需要一种方法来访问树中的所有节点。以下是遍历二叉树的一种常见方式——中序遍历。

中序遍历遵循“左-根-右”的顺序。其递归逻辑是：如果当前节点为空（`NULL`），则返回；否则，先递归遍历左子树，然后访问当前节点的数据，最后递归遍历右子树。

```c
void inorderTraversal(BTree root) {
    if (root == NULL) {
        return;
    }
    inorderTraversal(root->left);  // 遍历左子树
    printf("%c ", root->data);     // 访问根节点数据
    inorderTraversal(root->right); // 遍历右子树
}
```

通过这种方式，所有左子树的节点都会在右子树节点之前被访问。

---

## 构建二叉树：节点创建与初始化

要使用二叉树，我们首先需要能够创建节点。这涉及到从堆内存中动态分配空间。

我们使用 `malloc` 函数来为一个新节点分配内存。`sizeof(Node)` 运算符能确保我们获得足够存储一个 `Node` 结构体的内存空间。

```c
BTree createNode() {
    BTree newNode = (BTree)malloc(sizeof(Node));
    return newNode;
}
```

分配内存后，我们需要一个函数来初始化这个新节点的各个字段：数据、左指针和右指针。

```c
BTree initNode(DataType value, BTree leftChild, BTree rightChild) {
    BTree node = createNode();
    node->data = value;
    node->left = leftChild;
    node->right = rightChild;
    return node;
}
```

这个函数接收数据值和左右子树的指针作为参数，填充新节点的内容，并返回指向该节点的指针。

---

## 从数组递归构建完整二叉树

现在，我们将学习如何利用数组中的数据递归地构建一整棵二叉树。这是一种将线性数据转换为树形结构的有效方法。

`createTree` 函数递归地将数组元素构建成二叉树。其核心思想是利用完全二叉树的性质：对于数组中索引为 `i` 的元素，其左子节点在数组中的索引是 `2*i + 1`，右子节点索引是 `2*i + 2`。

以下是该函数的实现步骤：

1.  检查递归基线条件：如果当前索引 `i` 超出了数组大小 `size`，则返回 `NULL`。
2.  否则，为当前数组元素 `data[i]` 创建一个新节点。
3.  递归地为左子节点（索引 `2*i+1`）和右子节点（索引 `2*i+2`）调用 `createTree` 函数。
4.  将递归调用返回的子树指针赋值给当前节点的 `left` 和 `right` 成员。
5.  返回当前构建好的节点指针。

```c
BTree createTree(DataType data[], int i, int size) {
    if (i >= size) {
        return NULL; // 基线条件：超出数组范围
    }
    // 为当前数据创建节点，并递归创建其左右子树
    BTree leftChild = createTree(data, 2*i + 1, size);
    BTree rightChild = createTree(data, 2*i + 2, size);
    return initNode(data[i], leftChild, rightChild);
}
```

---

## 代码演示与执行结果

让我们通过一个具体的例子，将以上所有概念串联起来，看看它们是如何协同工作的。

在 `main` 函数中，我们首先创建一个包含5个字符的数组。

```c
int main() {
    DataType data[] = {'A', 'B', 'C', 'D', 'E'};
    int size = 5;
```

接着，我们调用 `createTree` 函数，从数组索引0开始构建二叉树。

```c
    BTree myTree = createTree(data, 0, size);
```

树构建完成后，我们使用 `inorderTraversal` 函数对这棵树进行中序遍历并打印结果。

```c
    printf("Inorder traversal: ");
    inorderTraversal(myTree);
    printf("\n");
    return 0;
}
```

**执行结果：**
当运行这段代码时，控制台会输出中序遍历的结果：`D B E A C`。如果你手动绘制并遍历这棵根据数组 `[A, B, C, D, E]` 构建的二叉树，会得到相同的顺序，这验证了我们代码的正确性。

---

## 总结

本节课中我们一起学习了二叉树在C语言中的实现。我们从定义节点结构和类型别名开始，讲解了中序遍历的递归方法。然后，我们深入探讨了如何使用 `malloc` 动态创建节点，以及如何从数组数据出发，递归地构建一整棵二叉树。最后，通过一个完整的代码示例，我们看到了这些部分如何组合在一起工作。

![](img/7c8ee3c98eaa3d85f6264138f036793b_3.png)

二叉树是一种极其重要的数据结构，因为它能使某些操作（如搜索）在**对数时间复杂度**内完成，相比之下，在普通数组中执行相同操作可能需要**线性时间复杂度**。因此，对于处理大量数据且需要高效查询的问题，二叉树是非常理想的选择。理解这些基础实现，将为学习更高级的数据结构和算法（例如在C++标准模板库中提供的树结构）打下坚实的基础。