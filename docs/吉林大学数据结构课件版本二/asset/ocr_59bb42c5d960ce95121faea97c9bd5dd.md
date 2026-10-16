# 回顾：一元多项式相加的单链表形式的算法

```
void add_poly(JD *pa,JD *pb)
{ JD *p,*q,*s,*r;
    int x;
    p=pa->next;
    q=pb->next;
    r=pa;
```