# 6.4 树和森林

# 6.4.1 树的存储结构

# 1、双亲表示法

+   - 实现：定义结构数组存放树的结点，每个结点含两个域：
+     - 数据域：存放结点本身信息
+     - 双亲域：指示本结点的双亲结点在数组中位置

```
typedef struct PTNode
{
    TElemType data;
    int parent;
}PTNode;
```

```
typedef struct
{
    PTNode nodes[MAX_TREE_SIZE];
    int r,n;
}PTree;
```