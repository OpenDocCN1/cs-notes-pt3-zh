# 5.6 AVL树

# AVL树（Balanced Binary Tree or Height-Balanced Tree）

AVL树或者是空二叉树，或者是具有如下性质的BST：

+   - 根节点的左、右子树高度之差的绝对值不超过1；
+   - 且根节点左子树和右子树仍然是AVL树。

# 节点的平衡因子BF（Balanced Factor）

一个节点的左子树与右子树的高度之差。

AVL树中的任意节点的BF只可能是-1，0和1。

AVL树的ASL可保持在O(log₂n)

# AVL树的查找操作

+   - 与BST的相同

![](bbox=[0.62, 0.55, 0.99, 0.95])