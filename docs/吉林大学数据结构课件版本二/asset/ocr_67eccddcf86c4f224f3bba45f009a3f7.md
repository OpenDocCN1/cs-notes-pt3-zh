# 双向循环链表插入 (在i之后)的动态过程

![](bbox=[0.06, 0.14, 0.95, 0.38])

非空表

结论：

```
p->next->prior = p = p->prior->next
```

在后继方向链入新结点：

```
s->next = p->next;
 p->next = s;
```