# 5.8 散列技术（Cont.）

冲突处理的方法----拉链法（链地址法）

+   开散列表的实现

+   存储结构定义

```
struct celltype{
    records data;
    celltype *next;
};/*链表结点类型*/
typedef celltype *cellptr;
/*开散列表类型，B为桶数*/
typedef cellptr HASH[B];
```

![](bbox=[0.65, 0.38, 0.99, 0.85])