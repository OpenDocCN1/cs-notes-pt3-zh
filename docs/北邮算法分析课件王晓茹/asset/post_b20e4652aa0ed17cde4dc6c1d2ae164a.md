
## Standard algorithm

```
for i ← 1 to n
    do for j ← 1 to n
        do c_ij ← 0
            for k ← 1 to n
                do c_ij ← c_ij + a_ik · b_kj
```

Running time = Θ(n³)

## Divide-and-conquer algorithm

IDEA:
$n\times n$ matrix = $2\times2$ matrix of $(n/2)\times(n/2)$ submatrices:

$\begin{bmatrix} r & s \\ t & u \end{bmatrix} = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \cdot \begin{bmatrix} e & f \\ g & h \end{bmatrix}$

$C = A \cdot B$

$r = ae + bg$
$s = af + bh$
$t = ce + dh$
$u = cf + dg$

8 mults of $(n/2)\times(n/2)$ submatrices
4 adds of $(n/2)\times(n/2)$ submatrices

## Analysis of D&C algorithm

T(n) = 8 T(n/2) + Θ(n²)

submatrix size

work adding submatrices

n^{log_b a} = n^{log_2 8} = n^3 ⇒ CASE 1 ⇒ T(n) = Θ(n^3).

No better than the ordinary algorithm.

## Strassen’s idea

- • Multiply 2×2 matrices with only 7 recursive mults.

P₁ = a · (f − h)
P₂ = (a + b) · h
P₃ = (c + d) · e
P₄ = d · (g − e)
P₅ = (a + d) · (e + h)
P₆ = (b − d) · (g + h)
P₇ = (a − c) · (e + f)

r = P₅ + P₄ − P₂ + P₆
s = P₁ + P₂
t = P₃ + P₄
u = P₅ + P₁ − P₃ − P₇

7 mults, 18 adds/subs.
Note: No reliance on commutativity of mult!

## Strassen's idea

- • Multiply 2×2 matrices with only 7 recursive mults.

P₁ = a · (f − h)
P₂ = (a + b) · h
P₃ = (c + d) · e
P₄ = d · (g − e)
P₅ = (a + d) · (e + h)
P₆ = (b − d) · (g + h)
P₇ = (a − c) · (e + f )

r = P₅ + P₄ − P₂ + P₆
= (a + d)(e + h)
+ d(g − e) − (a + b)h
+ (b − d)(g + h)
= ae + ah + de + dh
+ dg −de −ah −bh
+ bg + bh −dg −dh
= ae + bg

## Strassen’s algorithm

- 1. *Divide:* Partition *A* and *B* into *(n/2)×(n/2)* submatrices. Form terms to be multiplied using + and −.
- 2. *Conquer:* Perform 7 multiplications of *(n/2)×(n/2)* submatrices recursively.
- 3. *Combine:* Form *C* using + and − on *(n/2)×(n/2)* submatrices.

*T(n) = 7 T(n/2) + Θ(n²)*

## Analysis of Strassen

Hopcroft和Kerr已经证明\(T(n) \geq 2(n^2) \times 2\) 矩阵的乘积，7次乘法是必要的。因此，要想进一步改进矩阵乘法的时间复杂性，就不能再基于计算\(2 \times 2\)矩阵的7次乘法这样的方法了。或许应当研究 \(3 \times 3\) 或 \(5 \times 5\) 矩阵的更好算法。
The number 2.81 may not seem much smaller than 3, but because the difference is in the exponent, the impact on running time is significant. In fact, Strassen's algorithm beats the ordinary algorithm on today's machines for \(n \geq 30\) or so.

Best to date (of theoretical interest only): \(\Theta(n^{2.376 \cdots})\)。

## 通过例子来理解分治法

合并排序
分治法在排序中的应用！

## 排序:Sort

设 n 个记录的序列为 { R₁, R₂, R₃, …, Rₙ }

其相应的关键字序列为 { K₁, K₂, K₃, …, Kₙ }

若规定 1, 2, 3, …, n 的一个排列 p₁, p₂, p₃, …, pₙ，使相应的关键字满足如下非递减关系：

Kₚ₁ ≤ Kₚ₂ ≤ Kₚ₃ ≤ … ≤ Kₚₙ

则原序列变为一个按关键字有序的序列：

{ Rₚ₁, Rₚ₂, Rₚ₃, …, Rₚₙ }

此操作过程称为排序。

## 稳定排序与不稳定排序

假设 Kᵢ = Kⱼ ，且排序前序列中 Rᵢ 领先于 Rⱼ ；

若在排序后的序列中 Rᵢ 仍领先于 Rⱼ ，则称排序方法是稳定的。

若在排序后的序列中 Rⱼ 领先于 Rᵢ ，则称排序方法是不稳定的。

例，序列 3 15 8 8 6 9

若排序后得 3 6 8 8 9 15 稳定的

若排序后得 3 6 8 8 9 15 不稳定的

通俗地讲就是能保证排序前2个相等的数其在序列的前后位置顺序和排序后它们两个的前后位置顺序相同。

## 内部排序与外部排序

内部排序: 指的是待排序记录存放在计算机随机存储器中进行排序过程。

外部排序: 指的是待排序记录的数量很大，以致内存一次不能容纳全部记录，在排序过程中尚需对外存进行访问的排序过程。

## 排序的时间复杂度

排序过程主要是对记录的排序码进行比较和记录的移动过程。

因此排序的时间复杂度以算法执行中的数据比较次数及数据移动次数来衡量。

当一种排序方法使排序过程在最坏或平均情况下所进行的比较和移动次数越少，则认为该方法的时间复杂度就越好。

分析一种排序方法，不仅要分析它的时间复杂度，而且要分析它的空间复杂度、稳定性和简单性等。

## 内部排序

按照排序过程中所依据的原则的不同可以分类为：

- 插入排序
- 合并排序
- 快速排序

## 插入排序——直接插入排序

思想： 利用有序表的插入操作进行排序

有序表的插入：将一个记录插入到已排好序的有序表中，从而得到一个新的有序表。

例，序列 13 27 38 65 76 97

插入 49

13 27 38 49 65 76 97

![](img/18fa867d493fcce0c8a4a563c309db0a_153_0.png)

## 直接插入排序算法描述

初始，令第 1 个元素作为初始有序表；

依次插入第 2 , 3 , ..., k 个元素构造新的有序表；

直至最后一个元素；

例，序列 49 38 65 97 76 13 27

初始，S = { 49 } ；

{ 13 27 38 49 65 76 97 }

直接插入排序算法主要应用比较和移动两种操作。

```
void insertsort(ElemType R[],int n)
//待排序元素用一个数组R表示，数组有n个元素
{ for ( int i=1; i<n; i++) //i表示插入次数，共进行n-1次插入
{ ElemType temp=R[i]; //把待排序元素赋给temp
int j=i-1;
while ((j>=0)&&(temp<R[j]))
{ R[j+1]=R[j]; j--; } //顺序比较和移动
R[j+1]=temp;}
}
```

## 直接插入排序的效率分析

从空间来看，它只需一个元素的辅助空间，用于元素的位置交换。

从时间分析，首先外层循环要进行n-1次插入，每次插入：

- 最少比较一次（正序），移动两次；
- 最多比较i次，移动i+2次（逆序）（i=1，2，...，n-1）。

C<sub>min</sub>=n-1 M<sub>min</sub>=(n-1)×2;

C<sub>max</sub>=1+2+...+ (n-1) = (n<sup>2</sup>-n) /2

M<sub>max</sub>=3+4+...+ (n+1) = (n<sup>2</sup>+3n-4) /2

C<sub>ave</sub>= (n<sup>2</sup>+n-2) /4

M<sub>ave</sub>= (n<sup>2</sup>+7n-8) /4

因此，直接插入排序的时间复杂度为O（n<sup>2</sup>）。
