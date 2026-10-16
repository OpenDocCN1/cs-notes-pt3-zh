# 带头结点的出队的动态过程

![](bbox=[0.1, 0.15, 0.9, 0.52])

```
p = Q. front ->next;
Q. front->next = p->next;
free(p);
```