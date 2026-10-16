# 3.7 树型结构的应用（Cont.）

哈夫曼树的存储结构----静态三叉链表

```
typedef struct { /* 结点型 */
    double weight ; /* 权值 */
    int lchild ; /* 左孩子链 */
    int rchild ; /* 右孩子链 */
    int parent; /* 双亲链 */
} HTNODE ;
typedef HTNODE HuffmanT[ 2n-1 ] ;
```

|  | weight | parent | lchild | rchild |
|---|---|---|---|---|
| 0 |  |  |  |  |
| 1 |  |  |  |  |
| 2 |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
| (2n-1)-1 |  |  |  |  |

HuffmanT T;