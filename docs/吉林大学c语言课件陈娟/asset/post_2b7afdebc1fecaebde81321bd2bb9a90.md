
## （一）邻接表方法

设图G有k个结点，使用一个k*k的int型矩阵g表示图G，矩阵g的第i行顺序列出与结点i直接相连的结点编号，最后以“-1”结尾。则图G表示成右图的邻接表。

![](img/2c9b154d61523ac3dc02daf316966b8e_1341_0.png)

|   | 1 | 2 | -1 |   |   |   |   |   |
|---|---|---|---|---|---|---|---|---|
| 0 | 1 | 2 | -1 |   |   |   |   |   |
| 1 | 0 | 3 | 4 | -1 |   |   |   |   |
| 2 | 0 | 4 | 5 | -1 |   |   |   |   |
| 3 | 1 | 4 | -1 |   |   |   |   |   |
| 4 | 1 | 2 | 3 | 6 | 7 | -1 |   |   |
| 5 | 2 | 6 | 7 | -1 |   |   |   |   |
| 6 | 4 | 5 | -1 |   |   |   |   |   |
| 7 | 4 | 5 | -1 |   |   |   |   |   |

## （二）邻接矩阵方法

设图G有k个结点，使用一个k*k的bool类型矩阵g表示图G
矩阵元素

g[i, j] = { true 表示从结点 i 到结点 j 有直接路; false 表示从结点 i 到结点 j 没有直接路; }

利用这种表示法，左图的网表示成右图 8*8 的 bool 矩阵。

![](img/2c9b154d61523ac3dc02daf316966b8e_1342_0.png)

## 例12-5 找路径

已知一个网g=(v,e)。其中，

- v=(v1 ,v2 , ... ,vn) 为网g的结点集合,
- vi为网中结点。
- e={ (vi , vj)} 是网中边的集合,
- (vi ,vj)表示连接结点vi到结点vj的边。

找路径是指求从结点m到结点n的所有路径。

![](img/2c9b154d61523ac3dc02daf316966b8e_1344_0.png)

解:这样想该问题,

- 1. 从m点出发沿所有可能的路向前走一步;
- 2. 然后再站在新的点上，再向前走一步; ...

如此重复，直到走到结点n为止。
在走的过程中，保证不走重复点，可以得到下图的算法:

route

m:开始点； n:终结点； r:路迹数组p尾标

p[r] = m

m==n

输出p[0~r]

结束

m点的所有后继结点 i

i∈p[0~r]

route(i,n,r+1)

在该算法中，关键在于找出m点的所有后继点。

### (一) 邻接链表方法

![](img/2c9b154d61523ac3dc02daf316966b8e_1346_0.png)

设有如下声明：

```
#define h 10
struct node {
    int no;
    struct node *link;
};
int p[h];                 /* 踪迹数组 */
struct node *g[h];        /* 网的邻接链表 */
void printp( int,int );   // 函数原型：输出
bool iinp( int,int,int ); // 函数原型：判断
//点i是否已经走过（在P中）
```

```
void route ( int m, int n, int r ) {
 // 开始结点、终结点、路迹数组p的尾
struct node *hh;
int i;
p[r]=m;
if ( m==n )
printp(0,r);
else {
hh = g[m];
while ( hh!=NULL ) {
i = hh->no;
if ( !iinp(i,0,r) )
route(i,n,r+1);
hh = hh->link;
}
}
}
```

```
bool iinp( int ii,int u,int v ) {
    int j;
    for ( j=u; j<=v; j++ )
        if ( ii==p[j] )
            return true;
    return false ;
}
void printp( int e,int f ) {
    int j;
    for (j=e; j<=f; j++)
        printf("%4d", p[j] );
    printf("\n");
}
```

## 程序设计实例

- 一个排序算法
- 法雷序列
- 多项式加法

## 例12-2 排序算法

数组排序已经很熟悉，而且有各种各样的算法。下面用逐步增加递增子序列的方法实现链表排序。设有说明：

```
typedef ... datatype ;
struct item {
    datatype data ;
    int key ;
    struct item *next ;
};
typedef struct item *pt
```

以base为链首的链表如下图所示。该算法的思想是：

- 1. 开始假设空序列是递增的
- 2. 若i个元素子序列已经递增，则加一个元素，把插入到序列中一个适当位置使i+1个元素的子序列也递增
- 3. 直到i=n为止

![](img/2c9b154d61523ac3dc02daf316966b8e_1352_0.png)

## 开始

p = base

p!=NULL

使base~p递增

```
p0 = p；
p = p->next
```

return base

## 结束

## 使base~p递增

寻找p应该插入的位置r0,r

p插入到r0、r之间

## 结束

## 寻找位置

def

```
r = base
```

```
r->key<p->key
∧ r!=p
```

```
r0 = r;
r = r->next
```

## 结束

## p插入到
r0、r之间

def

```
r≠p
```

```
把p独立出来=>q ;
p指向p0
```

```
r ==
base
```

```
插入到链头:
q->next = base ; base = q
```

```
插入到r0,r之间:
q->next = r ; r0->next = q
```

## 结束

考察程序运行中各个参数、变量、链表的变化状态。如图所示：
设从base到p0之间的子链表已经递增，现在加入p所指示的节；
在base~p0之间查找合适位置，设应该把p所指的节插入到r0,r所之间；
把p独立出来=>q， p指向p0：
    q = p ;
    p0->next = p->next ;
    p = p0 ;
把p（现在由q指示）插入到r0,r之间：
    q->next = r ;
    r0->next = q;
现在链表结构是：

![](img/2c9b154d61523ac3dc02daf316966b8e_1355_0.png)

```
pt sort(pt base ) {        /* 链表排序，base 为链首 */
    pt p ,p0 ,r ,r0 ,q ;
    p0 = NULL ;
    p = base ;
    while ( p!=NULL ) {  /* 逐项处理，把p加入到子序列中，并保持 “base--p”递增 */
        r = base ;      /* 寻找位置 */
        while ( ( r->key < p->key ) && ( r!=p ) ) {
            r0 = r ;
            r = r-> next ;
        }
        if (r!=p) {  /* p插入到r0、r之间 */ /* 若 r==p ，在链尾，则不用插入 */
            q = p ;      /* 把 p 独立出来，令 q 指向它 */
            p0->next = p->next ;
            p = p0 ;
            if ( r == base ) {      /* 插入 */      /* 插在链首 */
                q->next = base ;
                base = q ;
            } else {      /* 插在链中r0、r之间 */
                q->next = r ;
                r0 -> next = q ;
            }
        }
        p0 = p ;      /* 前进一项 */
        p = p->next ;
    }
    return base ;
} /* sort */
```
