```
p=list;
for( i=1; i<=k-1; i++ )
{
    r=p;
    p=p->link;
}                         // 找到第一个出发点 //
while ( p->link != p )
{
    for(i=1; i<=m-1; i++)
    {
        r=p;
        p=p->link;
    }                         // 找到被删除结点(第m个结点) //
    printf( “%d”, p->data );
    r->link=p->link;          // 删除p所指的结点 //
    free(p);
    p=r->link;
}
printf( “%d”, p->data );
```