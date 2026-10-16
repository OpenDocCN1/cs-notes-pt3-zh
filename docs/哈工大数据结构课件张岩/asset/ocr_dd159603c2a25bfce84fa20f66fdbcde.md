# 3.2 二叉树（Cont.）

# 二叉树的复制

+   - 两株二叉树具有相同结构指：
+     - （1）它们都是空的；
+     - （2）它们都是非空的，且左右子树分别具有相同结构。

“形状”相同

+   - 相似二叉树:具有相同结构的二叉树为相似二叉树。

+   - 相似且对应结点包含相同信息的二叉树称为等价二叉树。

+   - 判断两株二叉树是否等价的算法：

```
struct node {
    struct node *lchild ;
    struct node *rchild ;
    datatype data ;
};
typedef struct node * BTREE;
```