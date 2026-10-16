# 出队

```
Status DeQueue(LinkQueue &Q, Qelemtype &e)
{
    //删除队头结点，并返回队头元素的值
    if (Q.front==Q.rear) return ERROR;    //判队空
    p = Q.front->next;
    e = p->data;                          //保存队头的值
    Q.front->next = p->next;              //新队头
    if (Q.front->next==NULL) Q.rear = Q.front;
    free(p);
    return OK;
}
```

注：与书中p62不同