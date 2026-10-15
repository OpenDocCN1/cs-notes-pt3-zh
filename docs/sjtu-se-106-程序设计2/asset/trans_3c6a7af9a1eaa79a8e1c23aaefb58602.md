

## 一个简单的 BST 实现

```
/*
 * Function: insertNode
 * Usage: insertNode(t, key);
 * -----------------------------
 * Inserts the specified key at the appropriate location in the
 * binary search tree rooted at t.  Note that t must be passed
 * by reference, since it is possible to change the root.
 */

void insertNode(Node * & t, string key) {
    if (t == NULL) {
        t = new Node;
        t->key = key;
        t->left = t->right = NULL;
        return;
    }
    if (key == t->key) return;
    if (key < t->key) {
        insertNode(t->left, key);
    } else {
        insertNode(t->right, key);
    }
}
```

## 练习：构建二叉搜索树

绘制执行以下代码后得到的 BST：

```
Node *colors = NULL;
insertNode(colors, "red");
insertNode(colors, "orange");
insertNode(colors, "yellow");
insertNode(colors, "green");
insertNode(colors, "blue");
insertNode(colors, "indigo");
insertNode(colors, "violet");
```

![](img/af430dff16b82a0fe61ce7dee05dcf9c_507_0.png)

## 遍历策略

- 编写一个对二叉搜索树中每个键执行某些操作的函数很容易，因为递归使得将该操作应用于每个子树变得简单。
- 键的处理顺序取决于相对于递归调用何时处理当前节点：
  - 如果在任一递归调用之前处理当前节点，结果是 *前序遍历*。
  - 如果在对左子树的递归调用之后但在对右子树的递归调用之前处理当前节点，结果是 *中序遍历*。在这种使用字符串作为键的简单 BST 实现中，键将按字典顺序出现。
  - 如果在完成两个递归调用之后才处理当前节点，结果是 *后序遍历*。后序遍历在尝试释放树中的所有节点时特别有用。

## 练习：前序遍历

![](img/af430dff16b82a0fe61ce7dee05dcf9c_509_0.png)

```
void preorderTraversal(Node *t) {
    if (t != null) {
        cout << t->key << endl;
        preorderTraversal(t->left);
        preorderTraversal(t->right);
    }
}
```

![](img/af430dff16b82a0fe61ce7dee05dcf9c_509_1.png)

## 练习：中序遍历

![](img/af430dff16b82a0fe61ce7dee05dcf9c_510_0.png)

```
void inorderTraversal(Node *t) {
    if (t != null) {
        inorderTraversal(t->left);
        cout << t->key << endl;
        inorderTraversal(t->right);
    }
}
```

![](img/af430dff16b82a0fe61ce7dee05dcf9c_510_1.png)

## 练习：后序遍历

![](img/af430dff16b82a0fe61ce7dee05dcf9c_511_0.png)

```
void postorderTraversal(Node *t) {
    if (t != null) {
        postorderTraversal(t->left);
        postorderTraversal(t->right);
        cout << t->key << endl;
    }
}
```

![](img/af430dff16b82a0fe61ce7dee05dcf9c_511_1.png)

## 平衡问题

- 理想情况下，包含迪士尼七个小矮人名字的二叉搜索树应该看起来像这样：
- 然而，如果你恰好按字母顺序输入名字，这棵树最终会变成一个简单的链表，其中所有左子树都为 NULL，右链接形成一条简单的链。在该树上运行的算法将以 O(N) 时间运行而不是 O(log N) 时间。
- 二叉搜索树是 *平衡* 的，如果其左右子树的高度相差最多为一，并且这两个子树本身也是平衡的。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_512_0.png)

## 说明 AVL 算法

- H
- He
- Li
- Be
- B
- C

![](img/af430dff16b82a0fe61ce7dee05dcf9c_514_0.png)

## 说明 AVL 算法

H

He

Li

Be

B

C

![](img/af430dff16b82a0fe61ce7dee05dcf9c_515_0.png)

## 说明 AVL 算法

- H
- He
- Li
- Be
- B
- C

![](img/af430dff16b82a0fe61ce7dee05dcf9c_516_0.png)

