
## Binary search 二分搜索技术

问题：给定已按升序排好序的n个元素a[0:n-1]，现要在这n个元素中找出一个特定元素x。

## 分析：

- 该问题的规模缩小到一定的程度就可以容易地解决；
- 该问题可以分解为若干个规模较小的相同问题；
- 分解出的子问题的解可以合并为原问题的解；
- 分解出的各个子问题是相互独立的。

分析：很显然此问题分解出的子问题相互独立，即在a[i]的前面或后面查找x是独立的子问题，因此满足分治法的第四个适用条件。

```
//分治法：二分搜索
public static int binarySearch(int [] a, int x, int n)
{
    // 在 a[0] <= a[1] <= ... <= a[n-1] 中搜索 x
    // 找到x时返回其在数组中的位置，否则返回-1
    int left = 0; int right = n - 1;
    while (left <= right)
    {
        int middle = (left + right)/2;
        if (x == a[middle]) return middle;
        if (x > a[middle]) left = middle + 1; //在右半部查找
        else right = middle - 1;             //在左半部查找
    }
    return -1; // 未找到x
}
```

## 算法复杂度分析：

每执行一次算法的while循环，待搜索数组的大小减少一半。
因此，在最坏情况下，while循环被执行了O(logn)次。循环体内运算需要O(1)时间，因此整个算法在最坏情况下的计算时间复杂度为O(logn)。

## Recurrence for binary search

T(n) = 1 T(n/2) + Θ(1)

## subproblems

subproblem size

work dividing
and combining

n^{log_b a} = n^{log_2 1} = n^0 = 1 ⇒ CASE 2 (k = 0)

⇒ T(n) = Θ(lg n).

## 时间复杂度

- O(n)>O(logn)
- 例如： n=10¹⁰

思考题：求数组的最大值和最小值。

思考：利用分治真的比直接求最大值、最小值的效率高吗？

## 再看分治算法

- 一般，分治算法常与递归方式结合；
- 一般，将问题分成两个子问题更合理，对于递归来说，分得太细对于效率和复杂性并无好处。

## Powering a number

**Problem:** Compute \(a^n\), where \(n \in \mathbb{N}\).

**Naive algorithm:** \(\Theta(n)\).

**Divide-and-conquer algorithm:**

\(a^n = \begin{cases} a^{n/2} \cdot a^{n/2} & \text{if } n \text{ is even;} \\ a^{(n-1)/2} \cdot a^{(n-1)/2} \cdot a & \text{if } n \text{ is odd.} \end{cases}\)

\(T(n) = T(n/2) + \Theta(1) \Rightarrow T(n) = \Theta(\lg n).\)

## 【Example】 Exponentiation: computing X^N.

```
long int Pow ( long int X, unsigned int N )
{
    long int P = 1;
    while ( N -- ) P *= X;
    return P;
}
T(N) = O(N)
```

```
long int Pow ( long int X, unsigned int N )
{
/* 1*/    if ( N == 0 )
/* 2*/        return 1;

/* 5*/    if ( IsEven( N ) )
/* 6*/        return Pow( X * X, N / 2 );
    else
/* 7*/        return Pow( X * X, N / 2 ) * X;
}
T(N) = O( log N )
```

## 通过例子来理解分治法

大整数乘法

提高效率？ 乘法减少？

## 大整数的乘法

- • 问题： X和Y都是n位的二进制整数，要计算他们的乘积XY。
- • 分治法： 将n位的二进制整数X和Y都分成2段，每段的长为n/2位。
- x= [ A | B ] y = [ C | D ]
- • 所以， X = A2n/2 + B, Y = C2n/2 + D  
  XY = AC 2n + (AD+BC) 2n/2 + BD

## 算法复杂性分析

- XY = AC 2ⁿ + (AD+BC) 2ⁿ/² + BD
  - 乘法次数：4次n/2位的整数乘法；
  - 加法次数：3次整数加法；
  - 移位次数：2次；
  - 当n>1时，有T(n)=4T(n/2)+O(n)
  - T(n)=O(n²)

算法复杂度：与小学算法没有改变

## 再接再厉

- XY = AC 2ⁿ + (AD+BC) 2ⁿ/² + BD
- XY = AC 2ⁿ + ((A-B)(D-C)+AC+BD) 2ⁿ/² + BD
  - 乘法次数：3次n/2位的整数乘法；
  - 加法：6次整数加法；
  - 移位：2次
  - 当n>1时，有T(n)=3T(n/2)+O(n)
  - T(n)=O(n^{log3})=O(n^{1.59})

## 大整数的乘法

请设计一个有效的算法，可以进行两个n位大整数的乘法运算

- ◆ 小学的方法： O(n²)
- ◆ 分治法：

![](img/18fa867d493fcce0c8a4a563c309db0a_136_0.png)

- 1. \( XY = ac \, 2^n + ((a-c)(b-d) + ac + bd) \, 2^{n/2} + bd \)
- 2. \( XY = ac \, 2^n + ((a+c)(b+d) - ac - bd) \, 2^{n/2} + bd \)

细节问题：两个XY的复杂度都是O(nlog³)，但考虑到a+c，b+d可能得到m+1位的结果，使问题的规模变大，故不选择第2种方案。

## 大整数的乘法

请设计一个有效的算法，可以进行两个n位大整数的乘法运算

- ◆小学的方法： O(n²)
- ◆分治法：O(n^1.59)
- ◆更快的方法??

- ✘效率太低
- ✓较大的改进

➤如果将大整数分成更多段，用更复杂的方式把它们组合起来，将有可能得到更优的算法。

➤最终的，这个思想导致了**快速傅利叶变换**(Fast Fourier Transform)的产生。该方法也可以看作是一个复杂的分治算法，对于大整数乘法，它能在**O(nlogn)**时间内解决。

➤是否能找到线性时间的算法？？？目前为止还没有结果。

## 通过例子来理解分治法

Strassen矩阵乘法
提高效率？ 乘法减少？

## Matrix multiplication

**Input:** \( A = [a_{ij}], B = [b_{ij}]. \quad \left\} \quad i, j = 1, 2, \dots, n. \)

**Output:** \( C = [c_{ij}] = A \cdot B. \)

\(\begin{bmatrix} c_{11} & c_{12} & \cdots & c_{1n} \\ c_{21} & c_{22} & \cdots & c_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ c_{n1} & c_{n2} & \cdots & c_{nn} \end{bmatrix} = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{n1} & a_{n2} & \cdots & a_{nn} \end{bmatrix} \cdot \begin{bmatrix} b_{11} & b_{12} & \cdots & b_{1n} \\ b_{21} & b_{22} & \cdots & b_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ b_{n1} & b_{n2} & \cdots & b_{nn} \end{bmatrix}\)

\( c_{ij} = \sum_{k=1}^{n} a_{ik} \cdot b_{kj} \)
