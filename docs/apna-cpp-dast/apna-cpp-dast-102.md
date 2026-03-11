# 102：根据前序遍历构建二叉搜索树

![](img/854225c5c58cfdc0bd40327bbdb7b2ba_0.png)

在本节课中，我们将学习如何根据给定的前序遍历序列，构建一个二叉搜索树。这是一个重要的数据结构问题，可以帮助我们理解二叉搜索树的特性和递归构建过程。

---

上一节我们介绍了二叉搜索树的基本概念，本节中我们来看看如何从前序遍历序列重建它。

## 问题描述

给定一个前序遍历序列，例如 `[6, 3, 1, 4, 8, 9]`，我们需要构建出对应的二叉搜索树，并返回其根节点。

## 核心思路

前序遍历的第一个元素总是二叉搜索树的根节点。利用二叉搜索树的性质：左子树的所有节点值小于根节点值，右子树的所有节点值大于根节点值。我们可以通过递归，为每个节点确定一个“上界”值，来界定其子树节点的取值范围。

## 算法步骤

以下是构建二叉搜索树的具体步骤：

1.  初始化一个索引 `i`，用于遍历前序序列。
2.  定义一个递归辅助函数，接收当前“上界”值作为参数。
3.  在递归函数中：
    *   如果索引越界或当前节点值超过上界，则返回空指针。
    *   否则，以当前节点值创建一个新节点作为根节点，并递增索引。
    *   递归构建左子树，上界值设为当前根节点的值。
    *   递归构建右子树，上界值保持不变（即传入的上界值）。
    *   返回构建好的根节点。

## 代码实现

以下是核心算法的C++代码实现：

```cpp
#include <vector>
#include <climits>
using namespace std;

// 二叉树节点定义
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

class Solution {
    // 递归辅助函数
    TreeNode* helper(vector<int>& preorder, int& i, int upper_bound) {
        // 基准情况：如果遍历完序列，或当前值超过上界
        if (i == preorder.size() || preorder[i] > upper_bound) {
            return nullptr;
        }
        
        // 创建当前节点（即根节点）
        int root_val = preorder[i];
        i++; // 移动到下一个元素
        TreeNode* root = new TreeNode(root_val);
        
        // 递归构建左子树，上界为当前根节点值
        root->left = helper(preorder, i, root_val);
        // 递归构建右子树，上界保持不变
        root->right = helper(preorder, i, upper_bound);
        
        return root;
    }
    
public:
    TreeNode* bstFromPreorder(vector<int>& preorder) {
        int i = 0; // 初始化索引
        // 初始上界设为整型最大值
        return helper(preorder, i, INT_MAX);
    }
};
```

## 复杂度分析

*   **时间复杂度**：**O(n)**，其中 `n` 是节点数量。每个节点恰好被访问一次。
*   **空间复杂度**：**O(h)**，其中 `h` 是树的高度。空间消耗主要来自递归调用栈。

---

![](img/854225c5c58cfdc0bd40327bbdb7b2ba_2.png)

本节课中我们一起学习了如何根据前序遍历序列构建二叉搜索树。我们利用了BST的性质和递归思想，通过为每个节点设定数值边界，高效地完成了树的构建。掌握这个方法对解决相关的树形结构问题非常有帮助。