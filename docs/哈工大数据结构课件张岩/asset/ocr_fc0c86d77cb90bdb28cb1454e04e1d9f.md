# 2.2线性表的存储结构---链接表（Cont.）

例：设计一个算法，遍历线性表，即按照线性表中元素的顺序，依次访问表中的每一个元素，每个元素只能被访问一次。

```
struct celltype {
    ElemType data;
    celltype *next;
}; /*节点型*/
typedef celltype *LIST;
/*线性表的型*/
typedef celltype *position;
/*位置型*/
```

```
void Travel( LIST L )
{
    position p;
    p = L->next;
    while ( p != NULL ) {
        cout << p->data;
        p = p->next;
    }
}
```

![](bbox=[0.03, 0.78, 0.98, 0.9])