# 链队列的主要操作

+   取队头元素

```
Status GetFront( LinkQueue Q, Qelemtype &e )
{
    if ( QueueEmpty(Q) ) return ERROR;
    e = Q.front->next->data;
    return OK;
}
```