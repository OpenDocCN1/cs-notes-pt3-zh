# 在静态链表中释放第 i 个结点

```
```c
int Remove ( SLinkList SL, int i ) {
    int p = Locate ( SL, i-1);
    if ( p == -1) return 0;      //找不到结点
    int q = SL.Nodes[p].link;    //第 i 号结点
    SL.Nodes[p].link = SL.Nodes[q].link;
    SL.Nodes[q].link = SL.newptr; //释放
    SL.newptr = q;
    return 1;
}
```
```