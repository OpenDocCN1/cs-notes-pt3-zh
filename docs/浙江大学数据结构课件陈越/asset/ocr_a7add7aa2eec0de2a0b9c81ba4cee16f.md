# ❖ **算法：** 将新增加结点插入到从其父结点到根结点的有序序列中

```
void insert( MaxHeap H, ElementType item )
{ /* 将元素item 插入最大堆，其中H->Elements[0]已经定义为哨兵 */
    int i;
    if ( IsFull(H) ) {
        printf("最大堆已满");
        return;
    }
    i = ++H->Size; /* i指向插入后堆中的最后一个元素的位置 */
    for ( ; H->Elements[i/2] < item; i/=2 )
        H->Elements[i] = H->Elements[i/2]; /* 向下过滤结点 */
    H->Elements[i] = item; /* 将item 插入 */
}
```

![](bbox=[0.407, 0.534, 0.896, 0.768])