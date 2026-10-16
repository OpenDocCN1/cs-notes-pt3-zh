```
Void createList_L (LinkList &L,int n )
{
    L = (LinkList) malloc (sizeof (LNode));
    L->next = NULL;  r=L;    //建立表头结点
    For(i=n;i>0;--i)
    {
        p = (LinkList) malloc (sizeof(LNode));
        scanf(&p->data );    //建立新结点
        r->next = p;    r =p;    //插入到表末端
    }
    r->next = NULL;
}
```