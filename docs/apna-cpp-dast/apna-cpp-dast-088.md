# 088：二叉树的第K层 🌳

![](img/ec69aa12b24ccc3786c6ad908130e893_0.png)

在本节课中，我们将学习如何解决一个关于二叉树的常见问题：打印出二叉树中第K层的所有节点。我们将使用递归的方法来实现这个功能，这种方法在二叉树问题中通常更简洁易懂。

## 概述

给定一个二叉树的根节点和一个整数K，我们的目标是打印出该二叉树在第K层上的所有节点值。我们约定，根节点位于第1层。例如，如果K=3，我们需要打印出第三层的所有节点。

## 问题分析与递归逻辑

上一节我们明确了问题目标，本节中我们来看看如何通过递归来解决它。

核心思路是：从根节点（第1层）开始，我们每向下一层，目标层数K就减1。当K减到1时，意味着我们到达了目标层，此时就可以打印当前节点的值。

以下是递归函数的核心步骤：

1.  **处理空节点**：如果当前节点为空（`root == NULL`），则直接返回，不做任何操作。
2.  **到达目标层**：如果当前层数`k == 1`，说明我们已经到达了需要打印的层，此时打印当前节点的值。
3.  **递归遍历**：如果还未到达目标层（`k > 1`），则分别对当前节点的左子节点和右子节点递归调用函数，并将目标层数`k`减1。

用伪代码描述这个逻辑：
```cpp
void printKLevel(Node* root, int k) {
    if (root == NULL) {
        return; // 基础情况：空节点
    }
    if (k == 1) {
        cout << root->data << " "; // 到达第K层，打印节点值
        return;
    }
    // 递归遍历左子树和右子树，层数k减1
    printKLevel(root->left, k - 1);
    printKLevel(root->right, k - 1);
}
```

## 代码实现与示例

理解了递归逻辑后，让我们将其转化为完整的C++代码并运行一个示例。

假设我们有如下二叉树：
```
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```
当`k=3`时，第3层的节点是4, 5, 6, 7。

以下是完整的函数实现：
```cpp
#include <iostream>
using namespace std;

// 二叉树节点结构
struct Node {
    int data;
    Node* left;
    Node* right;
    Node(int val) : data(val), left(nullptr), right(nullptr) {}
};

// 打印第K层节点的函数
void printKLevel(Node* root, int k) {
    if (root == NULL) {
        return;
    }
    if (k == 1) {
        cout << root->data << " ";
        return;
    }
    printKLevel(root->left, k - 1);
    printKLevel(root->right, k - 1);
}

// 主函数用于测试
int main() {
    // 构建示例二叉树
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);
    root->right->left = new Node(6);
    root->right->right = new Node(7);

    int k = 3;
    cout << "第 " << k << " 层的节点是: ";
    printKLevel(root, k);
    cout << endl;

    // 输出：第 3 层的节点是: 4 5 6 7
    return 0;
}
```

## 时间复杂度分析

该算法的时间复杂度是 **O(n)**，其中n是二叉树中的节点总数。在最坏情况下（例如，当K大于树的高度时），我们需要遍历树中的每一个节点。

## 总结

![](img/ec69aa12b24ccc3786c6ad908130e893_2.png)

本节课中我们一起学习了如何找出并打印二叉树中指定第K层的所有节点。我们使用了递归的方法，通过逐层递减目标层数K，并在K等于1时打印节点值来实现功能。这个方法逻辑清晰，代码简洁，是解决二叉树层相关问题的有效技巧。