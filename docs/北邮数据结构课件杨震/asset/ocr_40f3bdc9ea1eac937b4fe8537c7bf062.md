# 对用二叉链表表示的二叉树，设计一个算法，求其后序遍历的第一个结点。

```
typedef struct node {
etype data;
node *left, *right;
} node, *bitptr;
```

```
bitptr firstnode( bitptr root )
```