
# 第十讲 排序（下）

浙江大学 陈越

## 10.1 快速排序

### 算法概述

- 分而治之

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_401_0.png)

#### 分而治之

什么是快速排序算法的最好情况？  
每次正好中分 ➡️ T(N) = O( NlogN )

```c
void Quicksort( ElementType A[], int N )
{
    pivot = 从A[]中选一个主元;
    将S = { A[] \ pivot } 分成2个独立子集:
        A1={ a∈S | a ≤ pivot } 和
        A2={ a∈S | a ≥ pivot };
    A[] = Quicksort(A1,N1)∪
        {pivot}∪
        Quicksort(A2,N2);
}
```

### 选主元

令 pivot = A[0]？

1 2 3 4 5 6 ...... N-1 N

2 3 4 5 6 ...... N-1 N

3 4 5 6 ...... N-1 N

T(N) = O(N) + T(N-1)

= O(N) + O(N-1) + T(N-2)

= O(N) + O(N-1) + ... + O(1)

= O(N²)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_403_0.png)

### 子集划分

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_405_0.png)

- 如果有元素正好等于 `pivot` 怎么办？
  - 停下来交换？ ✓
  - 不理它，继续移动指针？

### 小规模数据的处理

- **快速排序的问题**
  - 用递归……
  - 对小规模的数据（例如 N 不到 100）可能还不如插入排序快
- **解决方案**
  - 当递归的数据规模充分小，则停止递归，直接调用简单排序（例如插入排序）
  - 在程序中定义一个 **Cutoff** 的阈值——课后去实践一下，比较不同的 **Cutoff** 对效率的影响

### 算法实现

```c
void Quicksort( ElementType A[], int Left, int Right )
{
    if ( Cutoff <= Right-Left ) {
        Pivot = Median3( A, Left, Right );
        i = Left; j = Right - 1;
        for( ; ; ) {
            while ( A[++i] < Pivot ) { }
            while ( A[--j] > Pivot ) { }
            if ( i < j )
                Swap( &A[i], &A[j] );
            else break;
        }
        Swap( &A[i], &A[ Right-1 ] );
        Quicksort( A, Left, i-1 );
        Quicksort( A, i+1, Right );
    }
    else
        Insertion_Sort( A+Left, Right-Left+1 );
}
```

## 10.2 表排序

### 算法概述

#### 间接排序

定义一个指针数组作为“表”（table）

| A | [0] | [1] | [2] | [3] | [4] | [5] | [6] | [7] |
|---|---|---|---|---|---|---|---|---|
| key | f | d | c | a | g | b | h | e |
| table | 3 | 5 | 2 | 1 | 7 | 0 | 4 | 6 |

如果仅要求按顺序输出，则输出：

A[ table[0] ], A[ table[1] ], ……，A[ table[N−1] ]

### 物理排序

#### N个数字的排列由若干个独立的环组成

| A | [0] | [1] | [2] | [3] | [4] | [5] | [6] | [7] |
|---|---|---|---|---|---|---|---|---|
| key | f | d | c | a | g | b | h | e |
| table | ③ | ⑤ | ② | ① | ⑦ | 0 | ④ | ⑥ |

Temp = f

如何判断一个环的结束？

```c
if ( table[i] == i )
```

### 复杂度分析

- 最好情况：初始即有序
- 最坏情况：
  - 有 ⌊N/2⌋ 个环，每个环包含 2 个元素
  - 需要 ⌊3N/2⌋ 次元素移动

T = O(mN)，m 是每个 A 元素的复制时间。

## 10.3 基数排序

### 举个例子

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_415_0.png)

### 桶排序

假设我们有 N 个学生，他们的成绩是0到100之间的整数（于是有 M = 101 个不同的成绩值）。如何在线性时间内将学生按成绩排序？

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_416_0.png)

```c
void Bucket_Sort(ElementType A[], int N)
{
    count[] 初始化;
    while (读入1个学生成绩grade)
        将该生插入count[grade]链表;
    for ( i=0; i<M; i++ ) {
        if ( count[i] )
            输出整个count[i]链表;
    }
}
```

T(N, M) = O(M+N)

### 基数排序

假设我们有 N = 10 个整数，每个整数的值在0到999之间（于是有 M = 1000 个不同的值）。还有可能在线性时间内排序吗？

输入序列：64, 8, 216, 512, 27, 729, 0, 1, 343, 125

用“次位优先”（Least Significant Digit）

T = O(P(N+B))

| Bucket | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|---|
| Pass 1 | 0 | 1 | 512 | 343 | 64 | 125 | 216 | 27 | 8 | 729 |
| Pass 2 | 0<br>1<br>8 | 512<br>216 | 125<br>27<br>729 |  | 343 |  | 64 |  |  |  |
| Pass 3 | 0<br>1<br>8<br>27<br>64 | 125 | 216 | 343 |  | 512 |  | 729 |  |  |

### 多关键字的排序

一副扑克牌是按2种关键字排序的

K⁰ [花色]：♣ < ♦ < ♥ < ♠

K¹ [面值]：2 < 3 < 4 < 5 < 6 < 7 < 8 < 9 < 10 < J < Q < K < A

有序结果：2♣ ... A♣，2♦ ... A♦，2♥ ... A♥，2♠ ... A♠

用“主位优先”（Most Significant Digit）排序：为花色建4个桶

在每个桶内分别排序，最后合并结果。

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_418_0.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_418_1.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_418_2.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_418_3.png)

![](img/8e26218ef88df8d6f4fe4ce3f83904a5_418_4.png)
