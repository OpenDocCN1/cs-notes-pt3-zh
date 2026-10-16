# 顺序表的删除(第i个位置的元素)

```
Status ListDelete_sq (SqList &L, int i, ElemType &e)
{
	if (i<1||i>L.length) return ERROR;
	P=&L.elem[i-1];
	e =*P;
	q= L.elem+ L.length–1 ;
	for(++p;p<=q;++p)
		*(p-1)=*p;
	--L.length;
	return OK;
}
```

//p为被删除元素位置

//被删除元素值赋值给e

//表尾元素位置

//被删除元素之后的元素左移