
```c
Polynomial PolyAdd (Polynomial P1, Polynomial P2)
{
    Polynomial front, rear, temp;
    int sum;
    rear = (Polynomial) malloc(sizeof(struct PolyNode));
    front = rear;
    while (P1 && P2) {
        switch (Compare(P1->expon, P2->expon)) {
        case 1:
            Attach(P1->coef, P1->expon, &rear);
            P1 = P1->link;
            break;
        case -1:
            Attach(P2->coef, P2->expon, &rear);
            P2 = P2->link;
            break;
        case 0:
            sum = P1->coef + P2->coef;
            if (sum) Attach(sum, P1->expon, &rear);
            P1 = P1->link;
            P2 = P2->link;
            break;
        }
    }
    for (; P1; P1 = P1->link) Attach(P1->coef, P1->expon, &rear);
    for (; P2; P2 = P2->link) Attach(P2->coef, P2->expon, &rear);
    rear->link = NULL;
    temp = front;
    front = front->link;
    free(temp);
    return front;
}
```

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_104_0.png)

```c
void Attach( int c, int e, Polynomial *pRear )
{
    /* 由于在本函数中需要改变当前结果表达式尾项指针的值， */
    /* 所以函数传递进来的是结点指针的地址，*pRear指向尾项*/
    Polynomial P;

    P =(Polynomial)malloc(sizeof(struct PolyNode)); /* 申请新结点 */
    P->coef = c;    /* 对新结点赋值 */
    P->expon = e;
    P->link=NULL;
    /* 将P指向的新结点插入到当前结果表达式尾项的后面 */
    (*pRear)->link = P;
    *pRear = P;   /* 修改pRear值 */
}
```

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_105_0.png)

## 3.1 树与树的表示

### 什么是树

分层次组织在管理上具有更高的效率！

数据管理的基本操作之一： 查找

如何实现有效率的查找？

### 查找（Searching）

查找：根据某个给定关键字K，从集合R中找出关键字与K相同的记录

- 静态查找：集合中记录是固定的
  - 没有插入和删除操作，只有查找
- 动态查找：集合中记录是动态变化的
  - 除查找，还可能发生插入和删除

### 静态查找

### 方法1：顺序查找

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_110_0.png)

```c
int SequentialSearch (StaticTable *Tbl,
                     ElementType K)
{ /*在表Tbl[1]~Tbl[n]中查找关键字为K的数据元素*/
    int i;
    Tbl->Element[0] = K;   /*建立哨兵*/
    for(i = Tbl->Length; Tbl->Element[i] != K; i--);
    return i; /*查找成功返回所在单元下标，不成功返回0*/
}
```

顺序查找算法的时间复杂度为 **O(n)**。

### 方法2：二分查找（Binary Search）

- 假设n个数据元素的关键字满足有序（比如：小到大）

  k₁ < k₂ < ... < kₙ

  并且是连续存放（数组），那么可以进行二分查找。

[例] 假设有13个数据元素，按关键字由小到大顺序存放。二分查找关键字为444的数据元素过程如下：

| 5 | 16 | 39 | 45 | 51 | 98 | 100 | 202 | 226 | 321 | 368 | 444 | 501 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |

left mid right

- 1、left = 1, right = 13; mid = (1+13)/2 = 7: 100 < 444;
- 2、left = mid+1=8, right = 13; mid = (8+13)/2 = 10: 321 < 444;
- 3、left = mid+1=11, right = 13; mid = (11+13)/2 = 12: 查找结束;

[例] 仍然以上面13个数据元素构成的有序线性表为例二分查找关键字为 43 的数据元素如下：

| 5 | 16 | 39 | 45 | 51 | 98 | 100 | 202 | 226 | 321 | 368 | 444 | 501 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 |

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_113_0.png)

- 1、left = 1, right = 13; mid = (1+13)/2 = 7: 100 > 43;
- 2、left = 1, right = mid-1= 6; mid = (1+6)/2 = 3: 39 < 43;
- 3、left = mid+1=4, right = 6; mid = (4+6)/2 = 5: 51 > 43;
- 4、left = 4, right = mid-1= 4; mid = (4+4)/2 = 4: 45 > 43;
- 5、left = 4, right = mid-1= 3; left > right ? 查找失败，结束;

### 二分查找算法

```c
int BinarySearch ( StaticTable * Tbl, ElementType K)
{
    /*在表Tbl中查找关键字为K的数据元素*/
    int left, right, mid, NotFound=-1;
    left = 1;
    right = Tbl->Length;
    while ( left <= right )
    {
        mid = (left+right)/2; /*计算中间元素坐标*/
        if( K < Tbl->Element[mid]) right = mid-1; /*调整右边界*/
        else if( K > Tbl->Element[mid]) left = mid+1; /*调整左边界*/
        else return mid; /*查找成功，返回数据元素的下标*/
    }
    return NotFound; /*查找不成功，返回-1*/
}
```

二分查找算法具有对数的时间复杂度O(logN)

### ❖ 11个元素的二分查找判定树

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_115_0.png)

- 判定树上每个结点需要的查找次数刚好为该结点所在的层数；
- 查找成功时查找次数不会超过判定树的深度；
- n个结点的判定树的深度为 `⌊log₂ n⌋+1`。
- ASL = (4*4+4*3+2*2+1)/11 = 3。

二分查找的启示？

### 树与非树？

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_117_0.png)

- 子树是不相交的；
- 除了根结点外，每个结点有且仅有一个父结点；
- 一棵N个结点的树有N-1条边。

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_117_1.png)
