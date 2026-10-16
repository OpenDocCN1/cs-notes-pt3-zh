
## Step 2: A recursive solution

A₁ A₂ A₃ A₄ A₅: (A₁ A₂ A₃)(A₄ A₅)?   (A₁ A₂)(A₃ A₄ A₅)? ……
A₁ (A₂ A₃)?   (A₁ A₂) A₃?

m[i,j] : the minimum # of scalar multiplications to compute Aᵢ..j; the cost of a cheapest way to compute A₁..n is m[1, n].
（令 m[i,j] 表示矩阵连乘 Aᵢ..j 的最小标量乘法的次数。则计算 A₁..n 所需的最少乘法次数为 m[1, n].）

If i = j, one matrix Aᵢ..i = Aᵢ, no scalar multiplications. Thus, m[i,i] = 0 for i = 1, 2, ..., n.
（若 i = j，只有 一个矩阵 Aᵢ，则没有矩阵元素相乘， m[i,i] = 0 for i = 1, 2, ..., n）

When i < j ?

m[i,j] : the minimum # of scalar multiplications to compute Aᵢ..j; the cost of a cheapest way to compute A₁..n is m[1, n].

When i<j, assuming that the optimal parenthesization splits Aᵢ Aᵢ₊₁… Aⱼ between Aₖ and Aₖ₊₁, where i≤k<j.

（当 i<j, 设矩阵连乘 Aᵢ..j 最优全括号的分割点位于 Aₖ 与 Aₖ₊₁ 之间，则...）

Then, m[i,j] = the minimum cost for computing Aᵢ..k
+ the minimum cost for computing Aₖ₊₁..j
+ the cost of multiplying Aᵢ..k and Aₖ₊₁..j

Recalling that Aᵢ has dimensions pᵢ₋₁ × pᵢ, then computing Aᵢ..k Aₖ₊₁..j takes pᵢ₋₁ pₖ pⱼ scalar multiplications. Thus, we obtain m[i,j]=m[i,k]+m[k+1,j]+pᵢ₋₁ pₖ pⱼ

A₁ A₂ A₃ A₄ A₅: (A₁ A₂ A₃)(A₄ A₅)?   (A₁ A₂)(A₃ A₄ A₅)? ……
    A₁(A₂ A₃)?   (A₁ A₂)A₃?

m[i,j]=m[i,k]+m[k+1,j]+p_{i-1}p_kp_j

- This recursive equation assumes that we know the value of k, which we actually do not know. （递归方程假设已知矩阵连乘最佳全括号问题的分隔点 k，实际上 k 是未知的。）
- Only j-i possible values for k, namely k=i, i+1, ..., j-1.
- The optimal parenthesization must use one of these values for k. Checking them all to find the best, we have
（最佳全括号中必定使用 {i, i+1, ..., j-1} 中的一个值作为 k）

m[i, j] = { 0 , if i = j,
 min_{i ≤ k < j} { m[i, k] + m[k + 1, j] + p_{i-1} p_k p_j }, if i < j. (15.12)

- The m[i,j] give the costs of optimal solutions to subproblems.

A₁ A₂ A₃ A₄ A₅: (A₁ A₂ A₃)(A₄ A₅)? (A₁ A₂)(A₃ A₄ A₅)? ……
A₁(A₂ A₃)? (A₁ A₂)A₃?

```
m[i, j] = { 0 , if i = j,
min_{i ≤ k < j} { m[i, k] + m[k + 1, j] + p_{i-1} p_k p_j }, if i < j. (15.12)
```

- Construct an optimal solution : Define s[i, j] to be a value of k at which we can split the product A_i A_{i+1}...A_j to obtain an optimal parenthesization. That is, s[i, j] equals a value k such that m[i, j] = m[i, k] + m[k+1, j] + p_{i-1} p_k p_j.

（构造最优解：定义 s[i,j] 为最佳全括号 A_i A_{i+1}...A_j 的分割位置 k 的值，即 s[i,j] = k，使得...）

## Step 3: Computing the optimal costs

$$m[i,j]=\begin{cases}0,&\text{if }i=j,\\\min_{i\le k<j}\{m[i,k]+m[k+1,j]+p_{i-1}p_kp_j\},&\text{if }i<j.\end{cases}$$

• It is a simple matter to write a **recursive algorithm** based on recurrence (15.12) to compute the minimum cost $m[1,n]$ for multiplying $A_1A_2\ldots A_n$. How?

```
RECURSIVE-MATRIX-CHAIN(p, i, j)
1  if i = j
2      return 0
3  m[i, j] ← ∞
4  for k ← i to j − 1
5      q ← RECURSIVE-MATRIX-CHAIN(p, i, k)
           + RECURSIVE-MATRIX-CHAIN(p, k + 1, j)
           + pᵢ₋₁pₖpⱼ
6      if q < m[i, j]
7          m[i, j] ← q
8  return m[i, j]
```

m[i, j] = { 0 , if i = j, min_{i ≤ k < j} { m[i, k] + m[k + 1, j] + p_{i-1} p_k p_j }, if i < j. (15.12)

```
RECURSIVE-MATRIX-CHAIN(p, i, j)
1 if i = j
2   return 0
3 m[i, j] ← ∞
4 for k ← i to j-1
5   q ← RECURSIVE-MATRIX-CHAIN(p, i, k)
    + RECURSIVE-MATRIX-CHAIN(p, k+1, j)
    + p_{i-1} p_k p_j
6   if q < m[i, j]
7     m[i, j] ← q
8 return m[i, j]
```

| cost |  |
|------|---|
| T(n) | T(1) ≥ 1 |
| 1    |  |
| 1    | T(n) ≥ 1 + |
| 1    | Σ_{k=1}^{n-1} (T(k) + T(n−k) + 1) |
| 1    |  |
| T(k) | = 2 Σ_{i=1}^{n-1} T(i) + n |
| T(n−k) |  |
| 1    | ≥ 2^{n-1} |
| 1    |  |
| 1    |  |
| 1    |  |

- This algorithm takes exponential time, which is no better than the brute-force method of checking each way of parenthesizing the product. Why?

A₁ A₂ A₃ A₄ A₅: (A₁ A₂ A₃)(A₄ A₅)? (A₁ (A₂ (A₃ A₄ A₅)))? ……
A₁(A₂ A₃)? (A₁ A₂)A₃?

m[i, j] = { 0 , if i = j,
 min_{i ≤ k < j} { m[i, k] + m[k + 1, j] + p_{i-1} p_k p_j }, if i < j. (15.12)

- # of subproblems: one problem for each choice of i and j satisfying 1≤i≤j≤n ? (所有子问题个数为 ?)

Cₙ² + n = Θ(n²)

1 ≤ i = j ≤ n, Cₙ¹ = n

1 ≤ i < j ≤ n, Cₙ² = n(n−1)/2
