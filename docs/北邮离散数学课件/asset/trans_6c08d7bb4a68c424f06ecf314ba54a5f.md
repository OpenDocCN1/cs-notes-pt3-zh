

## 证明（第 1 部分）

- 假设 $(x, y)$ 和 $(y, z)$ 都在 $R^\infty$ 中。证明 $(x, z)$ 也在 $R^\infty$ 中。
- 根据 $R^\infty$ 的定义，对某个 $m$，$(x, y) \in R^m$；对某个 $n$，$(y, z) \in R^n$。
- 于是 $(x, z) \in R^n R^m = R^{m+n}$，而 $R^{m+n}$ 包含在 $R^\infty$ 中。
- 因此，$R^\infty$ 必定是传递的。

## 证明（第 3 部分）

- 现在设 $S$ 是包含 $R$ 的任意传递关系；证明 $S$ 包含 $R^\infty$（也就是说，$R^\infty$ 是这种关系中最小的一个）。
- 因为 $R \subseteq S$，且 $S$ 是传递的，所以 $R^2 \subseteq S^2 \subseteq S$。
- 因此对所有 $n$，有 $R^n \subseteq S^n \subseteq S$。（为什么？）
- 因此 $S$ 必定包含 $R^\infty$，因为 $S$ 还必须包含 $R$ 的所有幂的并集。
- 证毕。
- 事实上，我们只需考虑长度不超过 $n$ 的路径。

## 示例 1

- 设
  - $A = \{1, 2, 3, 4\}$
  - $R = \{(1, 2), (2, 3), (3, 4), (2, 1)\}$
- 求 $R$ 的传递闭包。

![](img/c25dfd82fc242c2db53bc942dcad6885_1173_0.png)

$$M_R = \begin{bmatrix} 0 & 1 & 0 & 0 \\ 1 & 0 & 1 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 \end{bmatrix}$$

## 证明

$$R^{\infty} = \bigcup_{i=1}^{\infty} R^{i} = R \cup R^{2} \cup R^{3} \cup \dots$$

$$R^{\infty} = \bigcup_{i=1}^{n} R^{i} = R \cup R^{2} \cup \dots \cup R^{n}$$

若对于 $k \le n < m$，有

- $R^{m} \subseteq R^{k}$
- $(a, b) \in R^{m} \rightarrow (a, b) \in R^{k}$

则该等式成立。

设 $a$ 和 $b$ 在 $A$ 中，并假设 $a, x_1, x_2, \dots, x_{m-1}, b$ 是 $R$ 中从 $a$ 到 $b$ 的一条长度为 $m$ 的路径。

- $(a, x_1) \in R$
- $(x_1, x_2) \in R$
- $\dots$
- $(x_{m-1}, b) \in R$

路径中有 $m+1$ 个元素，但 $A$ 中只有 $n$ 个互不相同的元素。因此路径中必然存在某个重复顶点，设为 $x_i = x_j = c$，其中 $i < j$。

- $(a, x_1) \in R$
- $(x_1, x_2) \in R$
- $\dots$
- $(x_{i-1}, x_i) \in R$
- $(x_i, x_{i+1}) \in R$
- $\dots$
- $(x_{j-1}, x_j) \in R$
- $(x_j, x_{j+1}) \in R$
- $\dots$
- $(x_{m-1}, b) \in R$

红色边在该路径中形成一个回路；删除这个回路，就得到一条新路径。

删除回路后，从 $a$ 到 $b$ 的新路径为：

- $(a, x_1) \in R$
- $(x_1, x_2) \in R$
- $\dots$
- $(x_{i-1}, x_i) \in R$
- $(x_j, x_{j+1}) \in R$
- $\dots$
- $(x_{m-1}, b) \in R$

满足 $x_i = x_j = c$ 的从 $a$ 到 $b$ 的路径：

$$a, x_1, x_2, \dots, x_{i-1}, c, x_{j+1}, \dots, x_{m-1}, b$$

其长度为 $k = m - j + i$。

该过程可一直持续到 $k \le n$，于是有

- $R^{m} \subseteq R^{k}$
- $\forall m\ ((m > n \land (a, b) \in R^{m}) \rightarrow \exists k\ (k \le n \land (a, b) \in R^{k}))$

因此

$$R^{\infty} = \bigcup_{i=1}^{n} R^{i} = R \cup R^{2} \cup \cdots \cup R^{n}$$

证毕。

## 简单传递闭包算法

用 0-1 矩阵计算 $R^*$ 的算法。

procedure transClosure($\mathbf{M}_R$: n×n 0-1 matrix)

```text
A := B := M_R;
for i := 2 to n begin
    A := A ⊙ M_R;  B := B ∨ A    {join}
end    {note A represents R^i, B represents ⋃_{j=1}^i R^j}
return B {Alg. takes Θ(n^4) time}
```

## 一些定义

- $W_k$：一个布尔矩阵，其中 $1 \le k \le n$
  - 当且仅当以下条件成立时，$W_k$ 在位置 $i, j$ 处为 1：
  - 在 $R$ 中存在一条从 $a_i$ 到 $a_j$ 的路径，且其内部顶点（如果有）都来自集合 $\{a_1, a_2, \dots, a_k\}$
- $W_0$ 和 $W_n$ 又如何？
  - 令 $W_0 = W_R$
  - $W_n = W^{\infty}$
  - $W_0, W_1, W_2, \dots, W_n$

## Warshall 算法

- 过程
  - 从 $R$ 的矩阵开始，
  - 由前一个矩阵 $W_{k-1}$ 计算每个矩阵 $W_k$，
  - 在 $n$ 步后得到 $W^{\infty}$。

