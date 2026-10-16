# C程序

```
int LENGTH(struct node *list )
{
    struct node *p;
    int n;
    p=list;
    n=0;              // 链表的长度置初值0 //
    while (p!=NULL)
    {
        p=p→link;
        n++;
    }
    return(n);        // 返回链表的长度n //
}
```

![](bbox=[0.479, 0.035, 0.941, 0.249])