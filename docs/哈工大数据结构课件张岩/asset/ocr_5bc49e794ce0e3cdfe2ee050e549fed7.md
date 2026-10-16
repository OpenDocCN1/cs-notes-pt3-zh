# 2.2 线性表的存储结构---双向链表（Cont.）

插入操作：在带头结点的表中，在位置p插入元素x：

```
void Insert( ElemType x, position p, DLIST &L )
{
    s = new dcelltype;
    s->data = x;
    s->prior=p;
    s->next=p->next;
    p->next->prior=s;
    p->next=s;
}
```

![](bbox=[0.35, 0.55, 0.95, 0.88])

| prior | data | next |