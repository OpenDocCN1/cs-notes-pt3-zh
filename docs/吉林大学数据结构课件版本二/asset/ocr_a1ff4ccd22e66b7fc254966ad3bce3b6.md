# p-> exp= q-> exp （和x等于零） :插入结点的动态过程

pa
A
-1
7 0
3 1
9 2
5 17 ^
pb
B
-1
-9 2
22 7 ^
r
p
p
s
q

# 操作语句:

```
r->next=p->next;
free(p);    p=r->next;
s=q;        q=q->next;
free(s);
```