# 2.2 线性表的存储结构----一元多项式(Cont.)

算法Attch(c, e, d):

+   - 建立一个新结点，其系数coef=c，指数exp=e；并把它链到 d 所指结点之后，返回该结点指针。

```
polypointer Attch ( int c , int e , polypointer d )
{
  polypointer x ;
  x = new polynode ;
  x→coef = c ;
  x→exp = e ;
  d→link = x ;
  return x ;
}
```

![](bbox=[0.07, 0.2, 0.92, 0.3])

![](bbox=[0.07, 0.33, 0.92, 0.43])

![](bbox=[0.48, 0.65, 0.99, 0.85])