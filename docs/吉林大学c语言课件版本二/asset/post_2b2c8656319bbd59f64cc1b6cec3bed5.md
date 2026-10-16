
# （一）邻接表方法

设图G有k个结点，使用一个k*k的int型矩阵g表示图G，
矩阵g的第i行顺序列出与结点i直接相连的结点编号，最后以“-1”结尾。则图G表示成右图的邻接表。

![](img/e9111c49b068ca3c37fc762f47ecac61_990_0.png)

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

# （二）邻接矩阵方法

设图G有k个结点，使用一个k*k的bool类型矩阵g表示图G
矩阵元素

g[i, j] = { true    表示从结点 i 到结点 j 有直接路；
            false   表示从结点 i 到结点 j 没有直接路； }

利用这种表示法，左图的网表示成右图8*8的bool矩阵。

![](img/e9111c49b068ca3c37fc762f47ecac61_991_0.png)

|   | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|----|----|----|----|----|----|----|----|
| 0 |    | t | t |    |    |    |    |    |
| 1 | t  |    |    | t  | t  |    |    |    |
| 2 | t  |    |    |    | t  | t  |    |    |
| 3 |    | t  |    |    | t  |    |    |    |
| 4 |    | t  | t  | t  |    |    | t  | t  |
| 5 |    |    | t  |    |    |    | t  | t  |
| 6 |    |    |    |    | t  | t  |    |    |
| 7 |    |    |    |    | t  | t  |    |    |

# （三）邻接链表方法

设图G中有k个结点，使用一个有k个元素的一维指针数组G，数组G的第i个元素对应网中第i个结点。以它为链首，把与结点i直接相连的结点链成一个链。图G表示成右图的邻接链表：

![](img/e9111c49b068ca3c37fc762f47ecac61_992_0.png)

![](img/e9111c49b068ca3c37fc762f47ecac61_992_1.png)

# 例12-5 找路径

已知一个网g=(v,e)。其中，

- v=(v1 ,v2 , ... ,vn) 为网g的结点集合,
- vi为网中结点。
- e={ (vi , vj)} 是网中边的集合,
- (vi ,vj)表示连接结点vi到结点vj的边。

找路径是指求从结点m到结点n的所有路径。

![](img/e9111c49b068ca3c37fc762f47ecac61_993_0.png)

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

# (一) 邻接链表方法

![](img/e9111c49b068ca3c37fc762f47ecac61_995_0.png)

![](img/e9111c49b068ca3c37fc762f47ecac61_995_1.png)

设有如下声明：

```
#define h 10
struct node {
	int no;
	struct node *link;
};

int p[h]; /* 路迹数组 */
struct node *g[h]; /* 网的邻接链表 */
void printp( int,int ); // 函数原型：输出
bool iinp( int,int,int ) ; // 函数原型：判断
//点i是否已经走过（在P中）
```

```
void route ( int m, int n, int r ) {
    // 开始结点、终结结点、路迹数组p的尾
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

# 程序设计实例

- 一个排序算法
- 法雷序列
- 多项式加法

# 例12-2 排序算法

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

以base为链首的链表如下图所示。该算法的思想：

- 1. 开始假设空序列是递增的
- 2. 若i个元素子序列已经递增，则加一个元素，把插入到序列中一个适当位置使i+1个元素的子序列也递增
- 3. 直到i=n为止

![](img/e9111c49b068ca3c37fc762f47ecac61_1001_0.png)

开始

p = base

p!=NULL

return base

结束

使base~p递增

p0 = p ;
p = p->next

使base~p递增

寻找p应该插入的位置r0,r

p插入到r0、r之间

结束

# 寻找位置

def

```
r = base
```

r->key < p->key ∧ r != p

```
r0 = r;
 r = r->next
```

# 结束

# p插入到 r0、r之间

def

r != p

```
把p独立出来 => q ;
 p指向p0
```

r == base

```
插入到链头:
 q->next = base ; base = q
```

```
插入到r0,r之间:
 q->next = r ; r0->next = q
```

# 结束

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

![](img/e9111c49b068ca3c37fc762f47ecac61_1004_0.png)
