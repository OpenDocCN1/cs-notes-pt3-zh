# 093：二叉树的最大宽度

![](img/d966f6f51a2733b845627e355952ebf1_0.png)

## 概述
在本节课中，我们将学习如何计算二叉树的最大宽度。这是一个重要的数据结构问题，也是LeetCode上的第662号问题。我们将通过层序遍历和节点索引的概念来解决它。

## 什么是最大宽度？
最大宽度是指二叉树中任意一层的两个端点节点之间的最长距离。这里的“端点节点”是指该层最左边和最右边的非空节点，计算宽度时需要包含这两个节点本身。

## 核心概念与公式
为了计算宽度，我们需要为每个节点分配一个索引，类似于在完全二叉树中的索引方式。对于一个索引为 `i` 的节点：
*   其左子节点的索引为：`2 * i + 1`
*   其右子节点的索引为：`2 * i + 2`

某一层的宽度计算公式为：
`width = (该层最右节点索引 - 该层最左节点索引) + 1`

## 算法步骤
我们将使用层序遍历（广度优先搜索）来逐层处理节点。以下是算法的详细步骤：

1.  初始化一个队列，用于存储节点及其索引的配对。将根节点及其索引（通常设为0）入队。
2.  初始化一个变量 `maxWidth` 用于记录最大宽度，初始值为0。
3.  当队列不为空时，进行循环，每次循环处理一层：
    a.  获取当前层的节点数量 `levelSize`。
    b.  获取当前层队首节点的索引作为 `startIndex`（该层最左节点索引）。
    c.  获取当前层队尾节点的索引作为 `endIndex`（该层最右节点索引）。
    d.  根据公式计算当前层宽度：`currentWidth = endIndex - startIndex + 1`。
    e.  更新 `maxWidth = max(maxWidth, currentWidth)`。
    f.  遍历当前层的所有节点：
        *   弹出队首节点。
        *   如果该节点有左子节点，则将左子节点及其索引 `2 * i + 1` 入队。
        *   如果该节点有右子节点，则将右子节点及其索引 `2 * i + 2` 入队。
4.  循环结束后，返回 `maxWidth`。

## 代码实现
以下是基于上述逻辑的C++代码实现。注意，为了避免索引值过大导致整数溢出，我们使用 `unsigned long long` 类型来存储索引。

```cpp
#include <queue>
using namespace std;

struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode() : val(0), left(nullptr), right(nullptr) {}
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};

int widthOfBinaryTree(TreeNode* root) {
    if (root == nullptr) return 0;
    
    // 队列存储节点及其索引的配对
    queue<pair<TreeNode*, unsigned long long>> q;
    q.push({root, 0});
    
    unsigned long long maxWidth = 0;
    
    while (!q.empty()) {
        unsigned long long levelSize = q.size();
        unsigned long long startIndex = q.front().second; // 当前层最左节点索引
        unsigned long long endIndex = q.back().second;   // 当前层最右节点索引
        
        // 计算并更新最大宽度
        unsigned long long currentWidth = endIndex - startIndex + 1;
        if (currentWidth > maxWidth) {
            maxWidth = currentWidth;
        }
        
        // 处理当前层的所有节点
        for (unsigned long long i = 0; i < levelSize; ++i) {
            auto [node, index] = q.front();
            q.pop();
            
            // 将左子节点入队
            if (node->left != nullptr) {
                q.push({node->left, 2 * index + 1});
            }
            // 将右子节点入队
            if (node->right != nullptr) {
                q.push({node->right, 2 * index + 2});
            }
        }
    }
    
    return (int)maxWidth; // 根据题目要求返回int类型
}
```

## 复杂度分析
*   **时间复杂度：O(N)**，其中 N 是树中的节点数。我们需要访问每个节点一次。
*   **空间复杂度：O(W)**，其中 W 是树的最大宽度。在最坏情况下（完全二叉树），队列中最多会存储一层的所有节点。

![](img/d966f6f51a2733b845627e355952ebf1_2.png)

## 总结
本节课我们一起学习了如何计算二叉树的最大宽度。我们首先理解了宽度的定义，然后引入了完全二叉树索引的概念来辅助计算。核心算法是层序遍历，在遍历每一层时，通过记录该层首尾节点的索引来计算宽度。最后，我们实现了C++代码并分析了其复杂度。掌握这个方法，你就能高效解决此类二叉树宽度相关的问题。