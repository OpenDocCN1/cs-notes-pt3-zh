# 2.2线性表的存储结构----链表（Cont.）

操作的实现---- ①插入操作

```
① void Insert ( ElemType x, position p, LIST &L )
{
    position q;
    q = new celltype;
    q → data = x;
    q → next = p → next;
    p → next = q;
} //时间复杂性：O(1)
```

![](bbox=[0.045, 0.588, 0.951, 0.678])