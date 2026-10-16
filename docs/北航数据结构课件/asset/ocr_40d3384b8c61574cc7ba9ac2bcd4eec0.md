# 算法

# 寻找满足条件的结点

```
procedure DELETED( list, x )
    q←rlink(list)                                      // q初值指向头结点的下一个结点
    while (q≠list and data(q)≠x) do
        q←rlink(q)
    end                                                   // 找满足条件的链结点 //
    if (q=list) then
        [   print (‘There is no this node’)
            return   ]                                   // 没有找到满足条件的结点 //
    rlink(link(q))←rlink(q)
    llink(rlink(q))←llink(q)
    call RET(q)                                           // 释放被删除的结点的存储空间 //
    end
```

![](bbox=[0.075, 0.799, 0.778, 0.991])