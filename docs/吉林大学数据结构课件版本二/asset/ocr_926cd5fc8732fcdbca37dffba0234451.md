# 6.4.1 树的存储结构

# 3、孩子兄弟表示法（二叉树表示法）

+   - 实现：用二叉链表作树的存储结构，链表中每个结点的两个指针域分别指向其第一个孩子结点和下一个兄弟结点
+   - 特点
+     - 操作容易
+     - 破坏了树的层次

```
typedef struct CSNode
{
    TElemType data;
    struct CSNode *firstchild, *nextsibling;
}CSNode,*CSTree;
```