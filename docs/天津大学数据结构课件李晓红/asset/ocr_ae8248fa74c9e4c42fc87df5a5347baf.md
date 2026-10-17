# 例1. 搜索链表最后一个结点并打印其数值

```
void Search ( ListNode *f ) {
    if ( f->link == NULL )
        printf ( “%d\n”, f->data );
    else Search ( f->link );
}
```

![](bbox=[0.127, 0.572, 0.803, 0.856])