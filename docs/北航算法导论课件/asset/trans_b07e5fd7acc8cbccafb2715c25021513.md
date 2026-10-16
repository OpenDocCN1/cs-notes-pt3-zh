

## 30.3.1 迭代式 FFT 实现

```
RECURSIVE-FFT(a)
1  n = a.length
2  if n == 1
3      return a
4  ωₙ = e^(2πi/n)
5  ω = 1
6  a^[0] = (a₀, a₂, ..., aₙ₋₂)
7  a^[1] = (a₁, a₃, ..., aₙ₋₁)
8  y^[0] = RECURSIVE-FFT(a^[0])
9  y^[1] = RECURSIVE-FFT(a^[1])
10 for k = 0 to n/2 − 1
11     yₖ = yₖ^[0] + ω yₖ^[1]
12     yₖ₊(n/2) = yₖ^[0] − ω yₖ^[1]
13     ω = ω ωₙ
14 return y
```

![](img/09c68ab421cfce4995ddad1430ef2637_533_0.png)

y_k^[0] → • → + → y_k^[0] + ω_n^k y_k^[1]  y_k  (k = 0,1,...,n/2 −1)
ω_n^k →
 y_k^[1] → • → − → y_k^[0] − ω_n^k y_k^[1]  y_{k+n/2}

蝶形运算
对 y_k^[0] 加 t 和减 t

```
for k = 0 to n/2 − 1
    t = ω y_k^[1]
    y_k = y_k^[0] + t
    y_{k+(n/2)} = y_k^[0] − t
    ω = ω ω_n
```

- 使 FFT 算法在结构上采用迭代，而非递归。

```
RECURSIVE-FFT(a)
1  n = a.length
2  if n == 1
3    return a
4  ωₙ = e^(2πi/n)
5  ω = 1
6  a^[0] = (a₀, a₂, ..., aₙ₋₂)
7  a^[1] = (a₁, a₃, ..., aₙ₋₁)
8  y^[0] = RECURSIVE-FFT(a^[0])
9  y^[1] = RECURSIVE-FFT(a^[1])
10 for k = 0 to n/2 − 1
11    yₖ = yₖ^[0] + ω yₖ^[1]
12    yₖ₊(n/2) = yₖ^[0] − ω yₖ^[1]
13    ω = ω ωₙ
14 return y
```

RECURSIVE-FFT 的递归调用呈树形结构。

![](img/09c68ab421cfce4995ddad1430ef2637_534_0.png)

```
for k = 0 to n/2 − 1
  t = ω yₖ^[1]
  yₖ = yₖ^[0] + t
  yₖ₊(n/2) = yₖ^[0] − t
  ω = ω ωₙ
```

- **迭代** FFT 算法
- 将 *a* 的元素按照它们在叶节点中出现的顺序排列，

1) 用一次蝶形运算计算每一对元素的 DFT，并用该对的 DFT 替换该对元素，此时向量保存了 *n*/2 个 2 元素 DFT；

2) 将 *n*/2 个 DFT 两两分组，计算这四个向量元素的 DFT，需要 2 次蝶形运算，此时新向量保存了 *n*/4 个 4 元素 DFT；

3) 照此继续处理。

RECURSIVE-FFT 的递归调用呈树形结构。

![](img/09c68ab421cfce4995ddad1430ef2637_535_0.png)

```
for k = 0 to n/2 − 1
    t = ω y_k^[1]
    y_k = y_k^[0] + t
    y_{k+(n/2)} = y_k^[0] − t
    ω = ω ω_n
```

+   迭代 FFT 算法

初始 A[0.. n-1]

RECURSIVE-FFT 的递归调用呈树形结构。

```
ITERATIVE-FFT (a)
1 BIT-REVERSE-COPY (a, A)
2 n←length[a] // n is a power of 2.
3 for s←1 to lg n
4    m←2^s
5    ω_m←e^(2πi/m)
6    for k←0 to n-1 by m
7       ω←1
8       for j←0 to m/2 -1
9          t←ωA[k+j+m/2]
10         u←A[k+j]
11         A[k+j]←u+t
12         A[k+j+m/2]←u-t
13         ω←ω · ω_m
```

![](img/09c68ab421cfce4995ddad1430ef2637_536_0.png)

s=1
m=2^s=2
k=0, 2, ..., n-1
j=0
A[0] A[1]
A[2] A[3]
...

s=2
m=4
k=0, 4, ..., n-1
j=0, 1
A[0]  A[2]
A[1]  A[3]
...

s=3
m=8
k=0, 8, ..., n-1
j=0, 1, 2, 3
A[0]  A[4]
A[1]  A[5]
...

- 按位逆置换（Bit-reversal permutation）

```
ITERATIVE-FFT (a)
1 BIT-REVERSE-COPY (a, A)
...
```

原始顺序

![](img/09c68ab421cfce4995ddad1430ef2637_537_0.png)

按位逆置换

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|
| 000 | 001 | 010 | 011 | 100 | 101 | 110 | 111 |
| 000 | 100 | 010 | 110 | 001 | 101 | 011 | 111 |
| 0 | 4 | 2 | 6 | 1 | 5 | 3 | 7 |

# •  按位逆置换（Bit-reversal permutation）

原始顺序

![](img/09c68ab421cfce4995ddad1430ef2637_538_0.png)

按位逆置换

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---|---|---|---|---|---|---|
| 000 | 001 | 010 | 011 | 100 | 101 | 110 | 111 |
| 000 | 100 | 010 | 110 | 001 | 101 | 011 | 111 |
| 0 | 4 | 2 | 6 | 1 | 5 | 3 | 7 |

```
ITERATIVE-FFT(a)
1  BIT-REVERSE-COPY(a, A)
   ...
```

```
BIT-REVERSE-COPY(a, A)  // Θ(nlgn)
1  n ← length[a]
2  for k ← 0 to n−1                 // Θ(n)
3      do A[rev(k)] ← a_k           // Θ(lgn)
```

- 迭代 FFT 算法

```
ITERATIVE-FFT (a)
1 BIT-REVERSE-COPY (a, A)          // Θ(n lg n)
2 n ← length[a] // n is a power of 2.
3 for s ← 1 to lg n               // lg n
4     m ← 2^s
5     ω_m ← e^(2πi / m)
6     for k ← 0 to n-1 by m       // n/m = n/2^s
7         ω ← 1
8         for j ← 0 to m/2 -1     // m/2 = 2^s/2 = 2^(s-1)
9             t ← ω A[k+j+m/2]
10            u ← A[k+j]
11            A[k+j] ← u + t
12            A[k+j+m/2] ← u - t
13            ω ← ω · ω_m
```

L(n) = Σ_{s=1}^{lg n} (n / 2^s) 2^{s-1}
     = Σ_{s=1}^{lg n} n / 2
     = Θ(n lg n)

