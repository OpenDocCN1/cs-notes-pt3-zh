# 2.2线性表的存储结构----链表表（Cont.）

操作的实现----⑥ position Next( position p, LIST L )

```
position Next( position p, LIST L )
{
  position q ;
  if ( p→next == NULLL )
    cout<< "不存在后继元素";
  else {
    q = p →next;
    return q ;
  }
} //时间复杂度：O(1)
```

![](bbox=[0.05, 0.5, 0.95, 0.78])