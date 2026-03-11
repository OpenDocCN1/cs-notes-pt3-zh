# 090：根据前序和中序遍历构建二叉树 🌳

![](img/214b2683c99a2d8eda831aa33f3f463f_0.png)

在本节课中，我们将学习如何根据给定的前序遍历序列和中序遍历序列，唯一地重建一棵二叉树。这是二叉树相关的一个经典问题，也是理解递归和树遍历的关键。

## 概述

我们面临的问题是：给定一棵二叉树的**前序遍历**序列和**中序遍历**序列，要求重建出原始的二叉树结构。前序遍历的顺序是**根节点 -> 左子树 -> 右子树**，而中序遍历的顺序是**左子树 -> 根节点 -> 右子树**。通过这两个序列，我们可以唯一地确定二叉树的结构。

## 核心思路解析

上一节我们介绍了问题的定义，本节中我们来看看解决这个问题的核心逻辑。

前序遍历序列的第一个元素永远是当前子树的**根节点**。在中序遍历序列中找到这个根节点，其左侧的所有元素构成了**左子树**的中序遍历，右侧的所有元素构成了**右子树**的中序遍历。知道了左右子树的大小，我们就能在前序遍历序列中划分出对应的左右子树部分。然后，对左右子树递归地应用相同的过程，即可构建出整棵树。

以下是构建过程的关键步骤：

1.  **确定根节点**：前序序列的第一个值 `preorder[startPre]` 就是当前子树的根节点值。
2.  **在中序序列中定位根节点**：在中序序列 `inorder` 中找到该根节点的位置，记为 `inRootIndex`。
3.  **计算左子树大小**：左子树包含的节点数为 `inRootIndex - inStart`。
4.  **递归构建左子树**：
    *   左子树的前序序列范围：从 `preorder[startPre + 1]` 开始，长度为左子树大小的部分。
    *   左子树的中序序列范围：`inorder[inStart]` 到 `inorder[inRootIndex - 1]`。
5.  **递归构建右子树**：
    *   右子树的前序序列范围：紧接着左子树之后的部分。
    *   右子树的中序序列范围：`inorder[inRootIndex + 1]` 到 `inorder[inEnd]`。

## 代码实现

理解了核心思路后，我们来看看具体的代码实现。我们将创建一个递归的辅助函数来完成构建。

```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
private:
    // 辅助函数：在中序序列的指定区间 [inStart, inEnd] 内查找值的索引
    int findIndex(vector<int>& inorder, int inStart, int inEnd, int value) {
        for (int i = inStart; i <= inEnd; ++i) {
            if (inorder[i] == value) {
                return i;
            }
        }
        return -1; // 理论上根据输入有效性不会到达这里
    }

    // 主要的递归构建函数
    // preorder: 前序序列
    // preIndex: 当前要处理的前序序列元素的索引（通过引用传递，以便在递归中更新）
    // inorder: 中序序列
    // inStart, inEnd: 当前子树在中序序列中的区间
    TreeNode* buildTreeHelper(vector<int>& preorder, int& preIndex,
                              vector<int>& inorder, int inStart, int inEnd) {
        // 基准情况：如果区间无效，则返回空指针
        if (inStart > inEnd) {
            return nullptr;
        }

        // 步骤1：前序序列的当前元素是根节点
        int rootValue = preorder[preIndex];
        TreeNode* root = new TreeNode(rootValue);
        preIndex++; // 移动到下一个待处理的元素

        // 步骤2：在中序序列中找到根节点的位置
        int inRootIndex = findIndex(inorder, inStart, inEnd, rootValue);

        // 步骤3 & 4：递归构建左子树
        // 左子树的中序区间是 [inStart, inRootIndex - 1]
        root->left = buildTreeHelper(preorder, preIndex, inorder, inStart, inRootIndex - 1);

        // 步骤5：递归构建右子树
        // 右子树的中序区间是 [inRootIndex + 1, inEnd]
        root->right = buildTreeHelper(preorder, preIndex, inorder, inRootIndex + 1, inEnd);

        return root;
    }

public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        int preIndex = 0; // 从前序序列的第一个元素开始
        int n = inorder.size();
        return buildTreeHelper(preorder, preIndex, inorder, 0, n - 1);
    }
};
```

## 执行流程示例

让我们通过一个简单的例子来跟踪代码的执行。假设：
*   前序遍历 `preorder = [3, 9, 20, 15, 7]`
*   中序遍历 `inorder = [9, 3, 15, 20, 7]`

以下是构建过程的简要推演：

![](img/214b2683c99a2d8eda831aa33f3f463f_2.png)

1.  初始调用 `buildTree`，`preIndex = 0`，中序区间为 `[0, 4]`。
2.  根节点值为 `3` (`preorder[0]`)。在中序序列中找到 `3` 的索引为 `1`。
3.  递归构建左子树：
    *   中序区间为 `[0, 0]` (即元素 `9`)。
    *   创建节点 `9`，其左右子树区间无效，返回 `nullptr`。左子树构建完成。
4.  递归构建右子树：
    *   中序区间为 `[2, 4]` (即 `[15, 20, 7]`)。
    *   此时 `preIndex` 已更新为 `2`，根节点值为 `20`。
    *   在中序区间 `[2,4]` 中找到 `20` 的索引为 `2`。
    *   递归构建 `20` 的左子树（中序区间 `[2,1]` 无效，返回 `nullptr`）和右子树（中序区间 `[3,4]`，即 `[7]`）。
    *   构建 `7` 的节点，其左右子树均为 `nullptr`。
5.  最终，我们得到了正确的二叉树结构。

## 总结

本节课中我们一起学习了如何根据前序遍历和中序遍历序列构建二叉树。我们掌握了利用前序序列确定根节点，利用中序序列划分左右子树的核心思想，并通过递归函数实现了这一算法。理解这个过程对于深入掌握二叉树的结构和遍历方式至关重要。