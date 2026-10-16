# 2.4.1 队列的指针实现(Cont.)

队列的链接存储结构及实现

操作的实现----初始化和判空

```
① void MakeNull( QUEUE &Q )
{
    Q.front = new celltype ;
    Q.front → next = NULL ;
    Q.rear = Q.front ;
}
```

```
② Boolean Empty(QUEUE &Q)
{ if ( Q.front == Q.rear )
    return TRUE ;
else
    return FALSE ;
}
```

![](bbox=[0.14, 0.6, 0.36, 0.85])