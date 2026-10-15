

## 我们在哪里？

- 什么是动态规划
- 如何编写 DP 范式
  - 背包问题
  - 最长公共子序列
  - 矩阵链乘法
- 何时应用动态规划
- 练习

## 背包问题

![](img/a8f1b433a70f1e5c410c8b43e41b650e_799_0.png)

问题：背包
输入：物品集合 U = {u1,...,un}，大小为 s1,s2,...,sn，价值为 v1,v2,...,vn，以及背包容量 C
输出：可以放入背包中的最大价值

## 背包问题

如果小偷可以拿取物品的一部分呢？

![](img/a8f1b433a70f1e5c410c8b43e41b650e_800_0.png)

0-1 背包

## 背包问题

```
Algorithm 7.4 Knapsack
1. for i ← 0 to n do V[i, 0] ← 0
2. for j ← 0 to C do V[0, j] ← 0
3. for i ← 1 to n
4.   for j ← 1 to C
5.     V[i, j] ← V[i − 1, j]
6.     if sᵢ ≤ j then V[i, j] ← max{V[i, j], V[i − 1, j − sᵢ] + vᵢ}
7.   end for
8. end for
9. return V[n, C]
```

时间：Θ(nC)
空间：Θ(nC)

伪多项式算法

## 如何构造解？

![](img/a8f1b433a70f1e5c410c8b43e41b650e_803_0.png)

## 背包问题

如果小偷抢劫一家超市呢？可重复背包。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_804_0.png)

## 最长公共子序列

问题：LCS
输入：两个字符串 A=a1a2...an 和 B=b1b2...bm
输出：A 和 B 的最长公共子序列

L[i,j]：A[1..i] 和 B[1..j] 的最长公共子序列的长度

ababe

abcabc

解：L[n,m]

L[i,j] = { 0 if i = 0 or j = 0
L[i - 1, j - 1] + 1 if i > 0, j > 0 and a_i = b_j
max[L[i - 1, j], L[i, j - 1}] if i > 0, j > 0 and a_i ≠ b_j }

## LCS

L[i,j] = { 0 if i = 0 or j = 0
L[i-1,j-1] + 1 if i > 0, j > 0 and a_i = b_j
max{L[i-1,j], L[i,j-1]} if i > 0, j > 0 and a_i ≠ b_j }

![](img/a8f1b433a70f1e5c410c8b43e41b650e_806_0.png)

## LCS

### 算法 7.1 LCS

输入：长度为 n 和 m 的两个字符串 A 和 B，来自 Σ。

输出：A、B 的最长公共子序列的长度。

1. for i ← 0 to n do L[i,0] ← 0 end for
2. for j ← 0 to m do L[0,j] ← 0 end for
3. for i ← 1 to n
4. for j ← 1 to m
5. if a_i = b_j then L[i,j] ← L[i-1,j-1] + 1
6. else L[i,j] ← max{L[i-1,j], L[i,j-1]}
7. end if
8. end for
9. end for
10. return L[n,m]

时间：Θ(mn)
空间：Θ(max{m,n})

## 最长公共子串？

L[i,j]：a[1..i] 和 b[1..j] 的最长公共后缀的长度。

L[i,j] = { 0 if i = 0 or j = 0
L[i-1,j-1] + 1 if i > 0, j > 0 and a_i = b_j
0 if i > 0, j > 0 and a_i ≠ b_j }

解：所有 i>0 且 j>0 的最大 L[i,j]

## 矩阵链乘法

计算以下乘法的最 **高效** 方法是什么？

![](img/a8f1b433a70f1e5c410c8b43e41b650e_809_0.png)

乘法的顺序很重要。

## 测验

有多少种不同的方式来计算

M1 * M2 * ... * Mn

## 矩阵链乘法

问题：MCM
输入：矩阵链 M₁M₂...Mₙ，秩为 r₁r₂..rₙrₙ₊₁
输出：乘法的最小成本

ABCD

50,20,1,10,100

| 加括号方式 | 成本计算 | 成本 |
|---|---|---|
| A × {(B × C) × D} | 20·1·10 + 20·10·100 + 50·20·100 | 120,200 |
| (A × {B × C}) × D | 20·1·10 + 50·20·10 + 50·1·100 | 60,200 |
| (A × B) × (C × D) | 50·20·1 + 1·10·100 + 50·1·100 | 7,000 |

## 动态规划

C[i,j]：乘法 MiMi+1 ... Mj 的最小成本

```
C[i,j] = min_{i<k≤j}{C[i,k-1] + C[k,j] + r_i r_k r_{j+1}}
```

记忆化

|   | A | B | C | D |
|---|---|---|---|---|
| A | 0 | 1000 | 1500 | 7000 |
| B |  | 0 | 200 | 3000 |
| C |  |  | 0 | 1000 |
| D |  |  |  | 0 |

ABCD
50,20,1,10,100

## MCM

### 算法 7.2 MatChain

1. for i ← 1 to n
2. C[i,i] ← 0
3. end for
4. for d ← 1 to n − 1
5. for i ← 1 to n − d
6. j ← i + d
7. C[i,j] ← ∞
8. for k ← i + 1 to j
9. C[i,j] ← min{C[i,j], C[i,k−1] + C[k,j] + r[i]r[k]r[j+1]}
10. end for
11. end for
12. end for
13. return C[1,n]

∑_{d=1}^{n−1} ∑_{i=1}^{n−d} ∑_{k=1}^{d} c = (c n³ − c n)/6 = Θ(n³)

