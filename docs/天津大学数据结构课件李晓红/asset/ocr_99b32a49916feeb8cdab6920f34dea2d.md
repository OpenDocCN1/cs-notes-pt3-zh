# Status GetElem(SqList L,int i,ElemType &e)

+   • { // 初始条件： 顺序线性表L已存在， 1≤i≤ListLength(L)

+   • // 操作结果： 用e返回L中第i个数据元素的值

+   • if(i<1||i>L.length)

+   • exit(ERROR);

+   • e=*(L.elem+i-1);

+   • return OK;

+   • }