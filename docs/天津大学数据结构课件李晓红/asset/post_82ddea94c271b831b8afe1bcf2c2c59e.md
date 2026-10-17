
## C语言描述

```
Status ListInsert(SqList &L,int i,ElemType e)
{
    // 初始条件：顺序线性表L已存在，1≤i≤ListLength(L)+1
    // 操作结果：在L中第i个位置之前插入新的数据元素e，L的长度加1
    ElemType *newbase,*q,*p;
    if(i<1||i>L.length+1) // i值不合法
        return ERROR;
    if(L.length>=L.listsize) // 当前存储空间已满,增加分配
    {
        if(!(newbase=(ElemType
        *)realloc(L.elem,(L.listsize+LISTINCREMENT)*sizeof(ElemType))))
        exit(OVERFLOW); // 存储分配失败
        L.elem=newbase; // 新基址
        L.listsize+=LISTINCREMENT; // 增加存储容量
    }
    q=L.elem+i-1; // q为插入位置
    for(p=L.elem+L.length-1;p>=q;--p) // 插入位置及之后的元素右移
        *(p+1)=*p;
    *q=e; // 插入e
    ++L.length; // 表长增1
    return OK;
}
```

## 删除

![](img/04e8ddadedb998b3013c751f1cd77a21_47_0.png)

$$E_{dl}=\frac{1}{n}\sum_{i=0}^{n-1}(n-i-1)=\frac{1}{n}\cdot\frac{(n-1)n}{2}=\frac{n-1}{2}$$

### 顺序表的删除

```
int Delete ( SeqList &L, ListData x ) {
//在表中删除已有元素 x
int i = Find (L, x);    //在表中查找 x
if ( i >= 0 ) {
L.length -- ;
for ( int j = i; j < L.length; j++ )
L.data[j] = L.data[j+1];
return 1;    //成功删除
}
return 0;    //表中没有 x
}
```

### C语言描述

```
Status ListDelete(SqList &L,int i,ElemType &e) // 算法2.5
{
    // 初始条件： 顺序线性表L已存在， 1≤i≤ListLength(L)
    // 操作结果： 删除L的第i个数据元素， 并用e返回其值， L的长度减1
    ElemType *p,*q;
    if(i<1||i>L.length) // i值不合法
        return ERROR;
    p=L.elem+i-1; // p为被删除元素的位置
    e=*p; // 被删除元素的值赋给e
    q=L.elem+L.length-1; // 表尾元素的位置
    for(++p;p<=q;++p) // 被删除元素之后的元素左移
        *(p-1)=*p;
    L.length--; // 表长减1
    return OK;
}
```

## 顺序表的应用：集合的“并”运算

```
void Union ( SeqList &A, SeqList &B ) {
int n = Length ( A );
int m = Length ( B );
for ( int i = 0; i < m; i++ ) {
int x = GetData ( B, i ); //在B中取一元素
int k = Find ( A, x); //在A中查找它
if ( k == -1 ) //若未找到插入它
{ Insert ( A, x, n ); n++; }
}
}
```

### 集合的“交”运算

```
void Intersection ( SeqList &A, SeqList &B ) {
int n = Length ( A );
int m = Length ( B );
int i = 0;
while ( i < n ) {
int x = GetData ( A, i); //在A中取一元素
int k = Find ( B, x); //在B中查找它
if ( k == -1 ) { Delete ( A, i); n--; }
else i++; //未找到在A中删除它
}
}
```

## 链表（Linked List）

链表是线性表的链接存储表示

- 单链表
- 静态链表
- 循环链表
- 双向链表

### 单链表(Singly Linked List)

**定义：**用一组地址任意的存储单元存放线性表中的数据元素。

| 存储地址 | 数据域 | 指针域 |
|---|---|---|
| 1 | ZHANG | 13 |
| 7 | WANG | 1 |
| 13 | LI | null |
| 19 | ZHAO | 37 |
| 25 | WU | 7 |
| 31 | ZHOU | 19 |
| 37 | SUN | 25 |

![](img/04e8ddadedb998b3013c751f1cd77a21_53_0.png)

每个元素由结点(Node)构成，它包括两个域:数据域Data和指针域Link

![](img/04e8ddadedb998b3013c751f1cd77a21_54_0.png)

存储结构：链式存储结构

特点：存储单元可以不连续。

存取方式：顺序存取。

### 单链表的基本运算

**插入**

- **第一种情况：在第一个结点前插入**

```
newnode->link = first ;
first = newnode;
```

![](img/04e8ddadedb998b3013c751f1cd77a21_56_0.png)

![](img/04e8ddadedb998b3013c751f1cd77a21_56_1.png)

- **第二种情况：在链表中间插入**

```
newnode->link = p->link;
p->link = newnode;
```

![](img/04e8ddadedb998b3013c751f1cd77a21_57_0.png)

- **第三种情况：在链表末尾插入**

```
newnode->link = p->link;
p->link = newnode;
```

![](img/04e8ddadedb998b3013c751f1cd77a21_58_0.png)

完整插入函数：

```
int Insert ( LinkList& first, int x, int i ) {
//在链表第 i 个结点处插入新元素 x
ListNode * p = first; int k = 0;
while ( p != NULL && k < i - 1 )
{ p = p->link; k++; } //找第 i-1个结点
if ( p == NULL && first != NULL ) {
printf( "无效的插入位置!\n" );
return 0;
}
ListNode * newnode = //创建新结点
(ListNode *) malloc ( sizeof (ListNode) );
newnode->data = x;
if ( first == NULL || i == 1 ) { //插在表前
    newnode->link = first;
    first = newnode;
}
else { //插在表中或末尾
    newnode->link = p->link;
    p->link = newnode;
}
return 1;
}
```

**删除**

在单链表中删除 aᵢ 结点

```
q = p->link;
p->link = q->link;
```

![](img/04e8ddadedb998b3013c751f1cd77a21_61_0.png)

完整删除函数：

```
int Delete ( LinkList& first, int i ) {
    //在链表中删除第 i 个结点
    ListNode *p, *q;
    if ( i == 1 )              //删除表中第 1 个结点
    { q = first; first = first->link; }
    else {
        p = first; int k = 0;  //找第 i-1 个结点
        while ( p != NULL && k < i-1 )
        { p = p->link; k++; }
    }
}
```
