# 链表节点删除

```
1 t = x->next;
2 x->next = t->next;
3 free(t);
```

![](bbox=[0.15, 0.48, 0.85, 0.88])