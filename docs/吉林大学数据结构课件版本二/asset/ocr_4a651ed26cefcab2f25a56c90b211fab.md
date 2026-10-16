# 顺序表的插入

```
status ListInsert_sq ( SqList &L, int i , elemtype e)
//在表中第 i 个位置插入新元素 x
{
    if(i<1 || i>L.length+1)  return ERROR;
    if(L.length>=L.ListSize)
    {
        newbase=(elemtype*)realloc(L.elem,(L.listsize+L listincrement)*sizeof(elemtype));
        if(!newbase) exit(overflow);
        L.elem=newbase;
        L.listsize+=Listincrement;
    }
}
```