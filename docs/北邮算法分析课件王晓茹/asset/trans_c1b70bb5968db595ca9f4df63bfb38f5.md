

## 分析插入排序的稳定性

如果碰见一个和插入元素相等的，那么插入元素把想插入的元素放在相等元素的后面。所以，相等元素的前后顺序没有改变，从原无序序列出去的顺序就是排好序后的顺序，所以插入排序是稳定的。

直接插入算法的元素移动是顺序的，该方法是稳定的。

## 为什么强调“稳定性”？

## 插入排序的复杂性分析

- O(n²)
- 在这个算法中，大部分的时间都用在比较和挪动元素中，随着已经排好顺序的数组的增长，比较和被挪动的元素的个数也在增加，而且在整个过程中，很多元素不止挪动一次。

思考：如何用分治的思想解决问题？

## 基本思想

- 分解（divide）：
  - 将n个元素分成各含n/2个元素的子序列；
- 解决（Conquer）：
  - 递归地用合并排序法对两个子序列排序；
- 合并（Combine）：
  - 合并两个已经排好序的子序列。
  - 在对子序列排序时，其长度为1时递归结束。单个元素被视为是已经排好序的。

## 输入序列

## 输出序列

分解

合并

## MERGE-SORT

```
MERGE-SORT(A, p, r)
{
    if p < r
    {
        q = ((p+r)/2);
        MERGE-SORT(A, p, q);
        MERGE-SORT(A, q+1, r);
        MERGE(A, p, q, r);
    }
}
```

A: [2 4 5 7 1 2 3 6]

L: [2 4 5 7 ∞]

R: [1 2 3 6 ∞]

![](img/18fa867d493fcce0c8a4a563c309db0a_162_0.png)

```
MERGE(A, p, q, r)
{
1:    n1 = q-p+1;        //length(L)
2:    n2 = r-q;          //length(R)
3:    creat_arrays L[1...n1+1],R[1...n2+1];
4:    for i=1:n1
5:        do L[i] = A[p+i-1];
6:    for j=1:n2
7:        do R[j] = A[q+j];
8:    L[n1+1] = MAX;
9:    R[n2+1] = MAX;
10:   i = 1;
11:   j = 1;
12:   for k = p:r
13:   {
14:       if L[i] <= R[j]
15:       {
16:           A[k] = L[i];
17:           i = i+1;
18:       }
19:       else
20:       {
21:           A[k] = R[j];
22:           j = j+1;
23:       }
24:   }
}
```

# MERGE(A, p, q, r)

## 合并排序

**基本思想：** 将待排序元素分成大小大致相同的2个子集合，分别对2个子集合进行排序，最终将排好序的子集合合并成为所要求的排好序的集合。

```java
public static void mergeSort(Comparable a[], int left, int right)
{
    if (left<right) //至少有2个元素
    int i=(left+right)/2; //取中点
    mergeSort(a, left, i);
    mergeSort(a, i+1, right);
    merge(a, b, left, i, right); //合并到数组b
    copy(a, b, left, right);  //复制回数组a
}
}
```

用T(n)表示归并排序所用的时间，
并假定合并过程所用时间： cn，其中c是一个正数，则有

\(T(n) = \begin{cases} a & n = 1 \\ 2T(n/2) + cn & n > 1 \end{cases}\)

其中

**复杂度分析**

\(T(n) = \begin{cases} O(1) & n \leq 1 \\ 2T(n/2) + O(n) & n > 1 \end{cases}\)

T(n)=O(nlogn) 渐进意义下的最优算法

\(= 2^k T(1) + kcn\)

对于一般的整数n，我们可以假定 \(2^k < n \leq 2^{k+1}\)，于是，

\(T(n) \leq T(2^{k+1}), \quad T(n) = O(n \log n)\)

## 合并排序的灵活革新

基本思想：将待排序元素分成大小大致相同的2个子集合，分别对2个子集合进行排序，最终将排好序的子集合合并成为所要求的排好序的集合。

- 首先将长度为1的n个数组相邻元素两两配对，构成了长度为2的n/2个数组，合并时用比较算法对这每个子数组中元素进行排序；
- 再将这些长度为2的n/2个数组两两合并，构成了长度为4，个数为n/4的子数组，合并时用比较算法对每个子数组元素排序。
- 继续
- 直到形成长度为n，子数组个数=1的整个数组为止。

## 合并排序

算法mergeSort的递归过程可以消去。

![](img/18fa867d493fcce0c8a4a563c309db0a_167_0.png)

## 如何将两个有序段合并成一个有序段？

L
m m+1
r
1 3 6 7 2 4 5 8 9
i j

```
//合并算法
void Merge( Type c[], Type d[], int l, int m, int r)
{
    int i = l, j = m+1, k = l;
    while(( i <= m ) && ( j <= r ))
    {
        if ( c[i] <= c [j] ) d[k++] = c[i++];
        else d[k++] = c [j++];
    }
    if ( i > m )
    {
        for (int q = j; q <= r; q++)
            d[k++] = c[q];
    }
    else    for ( int q = i; q <= m; q++ )
        d[k++] = c[q];
}
```

```
//mergepass
void MergePass ( Type x[], Type y[], int s, int n )
{
    int i = 0;
    while ( i <= n - 2 * s )
    {//合并大小为s的相邻2段子数组
        Merge( x, y, i, i+s-1, i+2*s-1 );
        i = i + 2 * s;
    }
    //剩下的元素个数少于2s
    if ( i + s < n ) Merge ( x, y, i, i+s-1, n-1 );
    else for (int j = i; j <= n-1; j++)
        y[j] = x[j];
}
```

## //合并排序算法

```
void MergeSort ( Type a[], int n )
{
    Type *b = new Type [n];
    int s = 1;
    while ( s < n )
    {
        MergePass( a, b, s, n );
        s += s;
        MergePass( b, a, s, n );
        s += s;
    }
}
```

## 归并排序（Merge Sort）

- 算法分析
  - 最坏情况：归并排序是一个递归算法，所以很容易得到算法计算量的递推公式
  
  ```
  W(n) = W(⌊n / 2⌋) + W(⌈n / 2⌉)
  W(1) = 0
  ```
  
  所以算法最坏情况的复杂度为
  
  ```
  θ(n log n)
  ```
  
  - 算法需要 θ(n) 的辅助空间

## 合并排序（Merge Sort）

- 其他策略
  - 上面归并排序每次迭代时将原序列分割为两个基本等长的序列，称为二路归并排序
  - 也可以分割成其他的分，如3，4等等
- 评论：尽管合并排序最坏情况的比较次数比快速排序少，但它需要更多的元素移动，因此，它在实用中不一定比快速排序快。
- 分析合并排序的稳定性？

