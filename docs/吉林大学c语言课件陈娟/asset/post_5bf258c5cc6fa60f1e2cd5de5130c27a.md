
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

## 例12-3 法雷序列

对任意给定的自然数 n，把所有如下形式的不可约分数
\(\frac{j}{i}\)  \(\left(0 < i <= n ; 0 <= j <= i\right)\)

按递增顺序排列起来，称该序列为 n 级法雷序列 Fn。
例如F8 为：

0/1, 1/8, 1/7, 1/6, 1/5, 1/4, 1/7, 2/3, 1/8, 3/5, 2/7, 3/2, 1/4, 3/7, 5/8, 2/3, 5/7, 3/4, 5/5, 6/7, 7/8, 1/1

编函数，对任意给定的正整数 n，求 n 级法雷序列，并带回 n 级法雷序列链指针。

## 分析：

法雷序列的每项是个分数，不能用实数精确的表示，而且这些数的排列顺序是不规则的。用下图形式的链表来表示它。

![](img/2c9b154d61523ac3dc02daf316966b8e_1272_0.png)

struct farlei_item {
	int numerator , denominator ;
	struct farlei_item *next ;
};

typedef struct farlei_item *farleipointer ;

int gcd(int x, int y) { /* 求最大公约数 */
	if ( y==0 )
		return x ;
	else return gcd(y , x % y ) ;
}

/*构造法雷序列,并返回序列头指针*/
farleipointer farlei(int n) {
    int i,j;
    farleipointer fn , r , r0 , p;
    if( n<1 )                //如果n<=0,则没有法雷序列
        return NULL;
    /* 0/1 , 1/1 送入序列， fn指向链首 */
    fn = (farleipointer)malloc(sizeof(struct farlei_item));
                            //构造0/1
    fn->numerator = 0;
    fn->denominator = 1;
    fn->next = (farleipointer)
                malloc(sizeof(struct farlei_item)); //构造1/1
    fn->next->numerator = 1;
    fn->next->denominator = 1;
    fn->next->next = NULL;

/* 生成序列 */
for ( i=2; i<=n; i++ )
    for (j=1; j<i; j++)
        if ( gcd(i,j) == 1 ) { /* 查 j/i 位置 r0,r */
            r = fn ;
            while ( j*r->denominator > i*r->numerator ) {
                r0 = r ;
                r = r->next ;
            }
            /* j/i 插入到 r0,r 之间 */
            p = (farleipointer)malloc(sizeof(struct farlei_item));
            p->numerator = j ;
            p->denominator = i ;
            r0->next = p ;
            p->next = r ;
        }
    return fn ;
}

## 例12-4 多项式加法

p(x) = 6.5X⁵ + 3.4X² + X + 0.5

多项式可以用如下形式的链表来存储；

![](img/2c9b154d61523ac3dc02daf316966b8e_1277_0.png)

# 例如多项式

p(x) = 6.5 X^5 + 3.4 X^2 + X + 0.5

可以表示成如下形式：

![](img/2c9b154d61523ac3dc02daf316966b8e_1278_0.png)

编一个函数，实现多项式加法: p(X)+q(X) => s(X) 。

设有类型说明：

```
struct item {
    float coef;
    int exp;
    struct item *next;
};
typedef struct item *polynome;
```

解:在本程序的算法中，在链表上利用了一个哨兵项。所谓哨兵是在链表的链首多加一节，该节不存储有效的链表项的值，而保存一个边界值或空值，本程序的哨兵项是空值。由于利用了哨兵变量，所以处理统一了。多项式加法的算法如下图：

开始

(p!=NULL)
&&
(q!=NULL)

p ->exp
>
q ->exp

p => s ; p = p->next

p->exp
<
q->exp

q=>s; q = q->next

p+q=>s;
q = q->next;
p = p->next

p!=NULL

p=>s; p = p->next

q!=NULL

q=>s; q = q->next

结束

程序如下：

```
void adds( int exp0 , float coef0 , polynome r ) {
    /* 向s加入一项 */
    polynome r0;
    r0 = ( polynome)malloc( sizeof(struct item) );
    r0->exp = exp0;
    r0->coef = coef0;
    r0->next = NULL;
    r->next=r0;
}
```

```c
polynome addpolynome(polynome p, polynome q) {
polynome s , r

// s为结果多项式链首; r 起始指向结果多项式s的最低次幂项。
/* 申请一个哨兵变量，以便算法统一 */
s = (polynome)malloc( sizeof(struct item) );
r = s;
while ( (p!=NULL)&&(q!=NULL) ) /* 相加 */
if ( p->exp > q->exp ) {
    adds( p->exp , p->coef , r);
    p = p->next;
}else if ( p->exp < q->exp ) {
    adds( q->exp , q->coef , r);
    q = q->next;
}else{
    adds( p->exp , p->coef+q->coef , r);
    q = q->next; p = p->next;
}
}
r=r->next;
}
```
