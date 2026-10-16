# 单链表清空

```
Void make Empty ( LinkList L )
{
    //删除链表中除表头结点外的所有其它结点
    LNode *p;
    while ( L->next != NULL )
    {
        p = L->next;
        L->next = p->next;
        //将表头结点后第一个结点从链中摘下
        free( p );  //释放
    }
}
```