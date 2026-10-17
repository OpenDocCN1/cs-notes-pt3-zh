
## Problem statement

![](img/4208ee4325ab94ec0c685a689680f88f_196_0.png)

- A 1-1 map \((i, c_i)\) is called a subnet.
- Two subnets \((i, c_i)\) and \((j, c_j)\) are non-crossed if \(i < j\), then \(c_i < c_j\).
- The set \(MNS(i,j) = \{(u, c_u) \mid u \le i, c_u \le j\}\) is called a non-crossing set if, for all \((p, c_p)\) and \((q, c_q) \in MNS(i,j)\), \((p, c_p)\) and \((q, c_q)\) are non-crossed.
- Our goal is to find an \(MNS(n,n)\) with the maximum number of elements.
- Define \(size(i,j) = |MNS(i,j)|\).

## Derive the recursive equation

- Our goal is to maximize \(size(n,n)\).
- We have known that

\[
size(1,j)=\begin{cases}
0 & \text{if } j<c_1 \\
1 & \text{if } j\ge c_1
\end{cases} \tag{4}
\]

- We want to know the relationship between \(size(i,j)\) and \(size(i-1,j)\).
  - If \(j<c_i\), then \((i,c_i)\notin MNS(i-1,j)\), thus \(size(i,j)=size(i-1,j)\).
  - If \(j\ge c_i\), there are two cases.
    - Put \((i,c_i)\) into \(MNS(i-1,j)\), but \((i,c_i)\) might cross with items in \(MNS(i-1,j)\) or result in a smaller size, we have \(size(i,j)=size(i-1,j)\).

## Outline

- What is DP
- 0/1 Knapsack Problem
- Matrix Multiplication Chains
- All Pairs Shortest Path
- Maximum Non-crossing Subset of Nets
- Longest Common Subsequences

## Problem statements

### Definition 1: Subsequence

Given a sequence \(X = x_1x_2\ldots x_m\), another sequence \(Z = z_1z_2\ldots z_k\) is a subsequence of \(X\) if there exists a strictly increasing sequence \(i_1 < i_2 < \ldots < i_k\) of indices of \(X\) such that for all \(j = 1, 2, \ldots, k\), we have \(x_{i_j} = z_j\).

Example 1: If X = abcdefg, Z = abdg is a subsequence of X.

### Definition 2: Common subsequence

Given two sequences X and Y, a sequence Z is a common subsequence of X and Y if Z is a subsequence of both X and Y.

Example 2: X = abcdefg and Y = aaadgfd. Z = adf is a common subsequence of X and Y.

## Definitions

### Definition 3: Longest common subsequence: LCS

A **longest common subsequence** of X and Y is a common subsequence of X and Y with the longest length.

- The longest common subsequence may not be unique; for example, both `acd` and `abd` are LCSs of `abcd` and `acbd`.
- LCS has been successfully applied to many fields.
