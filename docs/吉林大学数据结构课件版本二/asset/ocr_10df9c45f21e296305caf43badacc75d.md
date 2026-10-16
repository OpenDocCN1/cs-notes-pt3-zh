# ▪ p-> exp= q-> exp（和x不等于零）：插入结点的动态过程

![](bbox=[0.01, 0.13, 0.97, 0.56])

# 操作语句:

```
p->coef=x;
r=p;    p=r->next;

s=q;    q=q->next;
free(s);
```