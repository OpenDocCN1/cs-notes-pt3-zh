
## 2.2 线性表的存储结构---静态链表（Cont.）

操作的实现--- ④插入操作

```
void Insert( ElemType x, position p, spacestr *SPACE )
{  position q;
  q = GetNode();
  SPACE[ q ].data = x;
  SPACE[ q ].next=SPACE[p ].next ;
  SPACE[ p ].next = q;
}
```

```
q = new celltype ;
q→data = x ;
q→next = p→next ;
p→next = q ;
```

|   | data | next |
|---|------|------|
| 0 | d    | 6    |
| 1 |      | 5    |
| 2 | c    | -1   |
| 3 | /--/ | 0    |
| 4 | a    | 10   |
| 5 |      | 8    |
| 6 | e    | -1   |
| 7 | /--/ | 4    |
| 8 |      | -1   |
| 9 | /--/ | 11   |
|10 | b    | 2    |
|11 |      | 12   |
|12 |      | 1    |
SPACE

L=7
M=3
avail=9

## 2.2 线性表的存储结构---静态链表（Cont.）

操作的实现--- ⑤删除操作

```
void Delete(position p, spacestr *SPACE)
{ position q ;
if ( SPACE[ p ].next != -1 ) {
    q = SPACE[ p ].next ;
    SPACE[ p ].next = SPACE[ q ].next ;
    FreeNode( q );
}
}
```

p→next !=NULL
q = p→next ;
p→next = q→next ;
delete q ;

|   | data | next |
|---|---|---|
| 0 | d | 6 |
| 1 |  | 5 |
| 2 | c | -1 |
| 3 | /--/ | 0 |
| 4 | a | 10 |
| 5 |  | 8 |
| 6 | e | -1 |
| 7 | /--/ | 4 |
| 8 |  | -1 |
| 9 | /--/ | 11 |
| 10 | b | 2 |
| 11 |  | 12 |
| 12 |  | 1 |
SPACE

L=7

M=3

avail=9

## 2.2 线性表的存储结构---双向链表

### 2.2.4 双向链表

双链表：

在单链表的各结点中再设置一个指向其前驱结点的指针域

示例：

![](img/ad2aee679abbcf477936d4ee2701e2d3_93_0.png)

结点结构：

![](img/ad2aee679abbcf477936d4ee2701e2d3_93_1.png)

优点：

- 实现双向查找（单链表不易做到）
- 表中的位置i可以用指示含有第i个结点的指针表示。

缺点：空间开销大。

## 2.2 线性表的存储结构----双向链表（Cont.）

存储结构定义：

```
struct dcelltype {
    ElemType data ;
    dcelltype *next, *prior ;
}; /* 节点类型 */
/* 表和位置的类型 */
typedef dcelltype *DLIST ;
typedef dcelltype *position ;
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_94_0.png)

![](img/ad2aee679abbcf477936d4ee2701e2d3_94_1.png)

## 2.2 线性表的存储结构---双向链表（Cont.）

插入操作：在带头结点的表中，在位置p插入元素x：

```
void Insert( ElemType x, position p, DLIST &L )
{
    s = new dcelltype;
    s->data = x;
    s->prior=p;
    s->next=p->next;
    p->next->prior=s;
    p->next=s;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_95_0.png)

| prior | data | next |

## 2.2 线性表的存储结构----单向环形链表

### 2.2.5 单向环形链表

# 单向环形链表

- 在(不带表头结点)的单向链表中，使末尾结点的指针域指向头结点，得到一个环形结构；用指向末尾结点的指针标识这个表。
- 示例： 空表R=NULL

![](img/ad2aee679abbcf477936d4ee2701e2d3_97_0.png)

# 结点结构：

- 同单链表

# 存储结构定义：

- 同单链表

## 2.2 线性表的存储结构----单向环形链表(Cont.)

在表左端插入节点 LInsert(x,R) → Insert(x,First(R),R)

```
void LInsert( Elementtype x , LIST &R )
{
    celltype *p;
    p = new celltype;
    p→data = x;
    if ( R == NULL )
    { p→next = p; R = p; }
    else
    { p→next = R→next; R→next = p; }
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_98_0.png)

## 2.2 线性表的存储结构----单向环形链表(Cont.)

在表右端插入节点 RInsert(x,R) → Insert(x,End(R), R)

```
void RInsert( ElemType x , LIST R )
{ LInsert ( x , R );
    R = R→next ;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_99_0.png)

## 2.2 线性表的存储结构----一元多项式

### 2.2.6 多项式的代数运算

多项式：$p(x)=3x^{14}+2x^8+1$

存储表示：采用单链表表示

示例：

![](img/ad2aee679abbcf477936d4ee2701e2d3_100_0.png)

存储结构定义：

```
struct polynode {
    int coef;  //系数
    int exp;   //指数
    polynode *link;  //指向下一项的指针
}; //结点类型

typedef polynode *polypointer;  //多项式的类型
```

| coef | exp | link |
|---|---|---|

## 2.2 线性表的存储结构----一元多项式(Cont.)

算法Attch(c, e, d):

- 建立一个新结点，其系数coef=c，指数exp=e；并把它链到 d 所指结点之后，返回该结点指针。

```
polypointer Attch ( int c , int e , polypointer d )
{
  polypointer x ;
  x = new polynode ;
  x→coef = c ;
  x→exp = e ;
  d→link = x ;
  return x ;
}
```

![](img/ad2aee679abbcf477936d4ee2701e2d3_101_0.png)

![](img/ad2aee679abbcf477936d4ee2701e2d3_101_1.png)

![](img/ad2aee679abbcf477936d4ee2701e2d3_101_2.png)

## 2.2 线性表的存储结构----一元多项式(Cont.)

多项式加法：

```
polypointer PolyAdd( polypointer a , polypointer b )
{  polypointer p, q, d, c ;
    int y ;
    p = a→link ;  q = b→link ;
    c = new polynode ;  d = c ;
    while ( (p != NULL) && (q != NULL) )
        switch ( Compare ( p→exp, q→exp ) )
        { case ‘=’ :
                y = p→coef + q→coef ;
                if ( y )  d = Attch( y, p→exp, d ) ;
                p = p→link ; q = q→link ;
                break ;
            case ‘>’ :
                d = Attch( p→coef, p→exp, d );
```
