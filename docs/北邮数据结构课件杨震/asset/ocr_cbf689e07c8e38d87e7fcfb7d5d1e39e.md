对于给定的不含头结点的单链表head，下面的程序过程实现了按结点值非降次序输出单链表中的所有结点。在每次输出一个结点时，就把输出结点从链表中删去。请在划线处填上适当的内容，使之成为一个完整的程序过程，每个空框只填一个语句。

```
void sort_output_delete (nodeptr head);
{
    nodeptr p,q,r,s;
    while( head != NULL)
    {
        p = NULL ; q= head; r= q ; s=q->next ;
        while ( s != NULL)
        {
            IF s->data < q->data
            { (1)____; (2)____; }
            r= s; (3)____;
        }
        printf(q->data);
        if (p==NULL)
            (4)____
        else (5)____;
        free (q);
    }
    ..........
}
```

![](bbox=[0.389, 0.573, 1.0, 0.965])