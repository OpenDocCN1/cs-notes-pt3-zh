# 2.2 线性表的存储结构----双向链表（Cont.）

存储结构定义：

```
struct dcelltype {
    ElemType data ;
    dcelltype *next, *prior ;
}; /* 节点类型 */
/* 表和位置的类型 */
typedef dcelltype *DLIST ;
typedef dcelltype *position ;
```

![](bbox=[0.3, 0.68, 0.65, 0.75])

![](bbox=[0.05, 0.78, 0.95, 0.9])