

## 又一些大作业或讨论题提示：

哈夫曼编码（用哈夫曼压缩方法，设计一个压缩软件）

活动安排

0-1背包；　分数背包

钢管切割；　ALS；　MCM；　LCS；　最短路径

OBST（最优二叉搜索树构建（以某本书里的词汇为基础？？））

雇佣（雇佣多少人）；取帽子；相同生日

RSA加密解密；　FFT；　串匹配；　计算几何；　最大流

算法实验室（问题求解工具、算法效果展示平台、多种算法时间复杂度对比分析、多种算法空间复杂度对比分析、IO导入、……。
支持穷举、递归、回溯、分治、DP、贪心；排序、查找；随机；图、树；等等若干方法（算法）的仿真演示。）

## Solution 16.2-2 ？？？？？

- Optimal substructure: 背包的最大负荷 W，有 n 件物品，最优解 S 中的最大项数为 i，则 S′=S-{i} 必定是最大负荷为 W-w_i，物品项为1,...,i-1 的最优解，且 v(S)=v(S′)+v_i
- c[i,w]: 物品项1,...,i，最大负荷 w 时的最优值？？？？？

c[i, w] = { 0                                 if i = 0 or w = 0,
                c[i-1, w]                       if w_i > w,
                max(v_i + c[i-1, w - w_i], c[i-1, w])   if i > 0 and w ≥ w_i. }

## Solution 16.2-2 ? ? ? ? ?

- 输入： W, n, v = <v₁, v₂..., vₙ>, w = <w₁, w₂..., wₙ>
- 储存c[i, j] 在表 c[0..n, 0..W]中（行优先）， c[n,W] 为原始最大值
- Tracing 最优解： If c[i,w]=c[i-1,w], item i is !∈ 最优解，继续 tracing with c[i-1,w], else item i ∈ 最优解，继续 tracing with c[i-1,w-wᵢ].

```
DYNAMIC-0-1-KNAPSACK(v,w, n,W)
for w ← 0 to W
    c[0,w] ← 0
for i ← 1 to n
    c[i, 0] ← 0
    for w ← 1 to W
        if wᵢ ≤ w
            if vᵢ + c[i-1,w-wᵢ] > c[i-1,w]
                c[i,w] ← vᵢ + c[i-1,w-wᵢ]
            else c[i,w] ← c[i-1,w]
        else c[i,w] ← c[i-1,w]
```

## 30 Polynomials and the FFT

A(x) = a₀x⁰ + a₁x¹ + ⋯ + aₙ₋₁xⁿ⁻¹ = Σⱼ₌₀ⁿ⁻¹ aⱼxʲ  and  B(x) = Σⱼ₌₀ⁿ⁻¹ bⱼxʲ

C(x) = A(x) + B(x)?

C(x) = A(x) · B(x)

- Straightforward method of adding two polynomials of degree n takes Θ(n) time
- Straightforward method of multiplying them takes Θ(n²) time
- Fast Fourier Transform (FFT, 【快速傅里叶变换算法】, can reduce the time to multiply polynomials to Θ(nlgn)
- Why? How?

## 30 Polynomials and the FFT

- FFT: the most common use is in signal processing
  - s(t): time domain 〔信号的时域表示〕
  - S(ω): frequency domain 〔频域〕

s(t) = sin(ωt) = sin(60πt)

f = 1/T = ω/(2π) = 60π/(2π) = 30

T: 周期，转一圈所需的时间
f: 频率，每秒转多少圈
ω: 角频率，每秒转多少（弧）度

S(ω) = ∫ e^(-iωt) s(t) dt

S(f) = ∫ e^(-i2πf t) s(t) dt

s(t) = sin(60πt) + sin(30πt)?

s(t) = sin(60πt) + sin(30πt) + sin(90πt)?

![](img/09c68ab421cfce4995ddad1430ef2637_483_0.png)

Run testSin.m

计算机科学中最重要的32个算法

## 30  Polynomials and the FFT

- **FFT: the most common use is in signal processing**
  - *s(t): time domain* 【信号的时域表示】
  - *S(w): frequency domain* 【频域】

![](img/09c68ab421cfce4995ddad1430ef2637_484_0.png)

## Polynomials

A(x) = Σ_{j=0}^{n-1} a_j x^j      x ∈ F, (R, C)

- polynomial coefficients : a₀, a₁, ..., aₙ₋₁ ∈ F.
- polynomial degree (维数) : A(x) is said to have degree k if its highest nonzero coefficient is a_k.
- polynomial degree-bound (维界) : any integer strictly greater than the degree.
- Therefore, the degree of a polynomial of degree-bound n may be any integer between 0 and n-1, inclusive.

## Polynomials addition （多项式相加）

- A(x), B(x), degree-bound n
- C(x) = A(x) + B(x), also degree-bound n

A(x) = Σ_{j=0}^{n-1} a_j x^j  and  B(x) = Σ_{j=0}^{n-1} b_j x^j

then  C(x) = Σ_{j=0}^{n-1} c_j x^j

where c_j = a_j + b_j for j = 0, 1, ..., n - 1.
For example, if the polynomials A(x) = 6x³+7x²-10x+9
and      B(x) = -2x³+4x-5,
then      C(x) = 4x³+7x²-6x+4.

- Running time: T(n) = Θ(n)

## Polynomials multiplication（多项式相乘）

- $A(x), B(x)$, degree-bound $n$
- $C(x)=A(x)B(x)$, degree-bound $2n-1$

For example, multiply $A(x)=6x^3+7x^2-10x+9$ and $B(x)=-2x^3+4x-5$

```
        6x³ + 7x² − 10x + 9
×      −2x³       + 4x − 5
────────────────────────────
       30x³ − 35x² + 50x − 45
  24x⁴ + 28x³ − 40x² + 36x
− 12x⁶ − 14x⁵ + 20x⁴ − 18x³
────────────────────────────
− 12x⁶ − 14x⁵ + 44x⁴ − 20x³ − 75x² + 86x − 45
```

- **Running time:** $T(n)=\Theta(n^2)$

## Polynomials multiplication〔多项式相乘〕

- **A(x), B(x), degree-bound n**    $A(x)=\sum_{j=0}^{n-1} a_j x^j$ and $B(x)=\sum_{j=0}^{n-1} b_j x^j$
- **C(x) = A(x)B(x), degree-bound 2n-1**

Another way to express the product C(x) is

$C(x)=\sum_{j=0}^{2n-2} c_j x^j$    (30.1)

where $c_j = \sum_{k=0}^{j} a_k b_{j-k}$    (30.2)

Note that degree(C) = degree(A) + degree(B), implying degree-bound(C) = degree-bound(A) + degree-bound(B) -1 ≤ degree-bound(A) + degree-bound(B). We also say: degree-bound(C)=degree-bound(A)+degree-bound(B)

