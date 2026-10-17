# 在静态链表第 i 个结点处插入一个新结点

```
int Insert ( SLinkList SL, int i, ListData x ) {
    int p = Locate ( SL, i-1);
    if ( p == -1 ) return 0;        //找不到结点
    int q = SL.newptr;              //分配结点
    SL.newptr = SL.Nodes[SL.newptr].link;
    SL.Nodes[q].data = x;
    SL.Nodes[q].link = SL.Nodes[p].link;
    SL.Nodes[p].link = q;            //插入
    return 1;
}
```