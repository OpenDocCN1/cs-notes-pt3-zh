# 5.2 线性查找（Cont.）

单向表上的查找——也适合于动态查找

+   - 单向表的类型定义

```
struct celltype {
    records data ;
    celltype * next ;
};
typedef celltype *LIST ;
```

+   - INSERT操作的实现

+   - DELETE操作的实现

```
LIST SEARCH(keytype k, LIST F)
/*在不带表头的单向链表中查找关键字为k 的记录，返回其指针*/
{
    LIST p = F ;
    while ( p != NULL )
        if ( p->data.key == k )
            return p ;
        else
            p = p->next ;
    return p ;
}
```

+   - 时间复杂度 O(n)； ASL成功=(n+1)/2， ASL失败=n+1