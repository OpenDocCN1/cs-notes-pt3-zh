

![](img/c25dfd82fc242c2db53bc942dcad6885_1591_0.png)

- 找到集合 {v1, v2, v4, v5, v6, v8} 的相邻顶点集合，其为 {v3, v7, v9, v11}
- 找到从 v1 到集合中顶点的长度。
  - l3 = min{8, l6 + d36} = {8,7} = 7
  - l7 = min{l4 + d47, l6 + d67} = min{10,10} = 10
  - l9 = min{l8 + d89, l6 + d69, l5 + d59} = min{10,10} = 10
  - l11 = 14
- Min{l3, l7, l9, l11} = l3 = 7
- 将 v6 连接到 v3

## Step 7

- 继续
  - 将 $v_3$ 连接到 $v_7$
  - 将 $v_7$ 连接到 $v_{10}$
  - 将 $v_{10}$ 连接到 $v_9$
  - 将 $v_9$ 连接到 $v_{11}$
- 那么从 $v_1$ 到 $v_{11}$ 的路径即为答案。
- 同时，我们也得到了从 $v_1$ 到图中其他顶点的最短路径。

## Finding the shortest path between any two vertices

- Distance Matrix: 设 G 是一个具有 n 个顶点的图。G 的距离矩阵为 D=(d_ij)_{n×n}
  - d_ij 表示边 (v_i, v_j) 的权重
  - 如果 v_i 和 v_j 之间没有边则 d_ij=∞
  - 设 D²=D*D= (d_ij²)_{n×n}
  - d_ij²=min{d_i1+d_1j, d_i2+d_2j, …, d_in+d_nj}
    - d_ij² 是从 v_i 到 v_j 经过两条边的最短路径长度。
  - 同理 D^k=D^{k-1}*D= (d_ij^k)_{n×n}
    - d_ij^k 是从 v_i 到 v_j 经过 k 条边的最短路径长度。

## Example 2

- 这是一个城市的图。求从 v₁ 到图中其他顶点的最短路径。

![](img/c25dfd82fc242c2db53bc942dcad6885_1595_0.png)

## Step 1

- 选择以 \(v_1\) 为根的有根树
- 用到 \(v_1\) 的长度标记每个顶点

![](img/c25dfd82fc242c2db53bc942dcad6885_1596_0.png)

## Step 2

- 用 l_i 表示树中从 v_1 到 v_i 的长度。
- 如果图中的边 (i,j) 不在树中，用 d_ij 表示从 v_i 到 v_j 的长度。
- 如果对所有这些边都有 l_j ≤ l_i + d_ij，则树给出答案，否则
- l_j > l_i + d_ij
  - 删除以 v_j 结束的边，
  - 在树中添加 (v_i,v_j)
  - 修改其影响的顶点的长度。

## Step 3

- 重复步骤直到找到答案。

![](img/c25dfd82fc242c2db53bc942dcad6885_1603_0.png)

## Define ⊕

- 设 $A = (a_{ij})_{n\times n}$, $B = (b_{ij})_{n\times n}$
- $C = A \oplus B = (c_{ij})_{n\times n}$
  - $c_{ij} = \min(a_{ij}, b_{ij})$
- $P = D \oplus D^2 \oplus D^3 \oplus ... \oplus D^n$
  - $p_{ij} = (p_{ij})_{n\times n}$
  - $p_{ij}$ 表示从 $v_i$ 到 $v_j$ 的最短长度

$D^3 = \begin{bmatrix} \infty & \infty & 4 & 4 \\ \infty & \infty & \infty & 5 \\ \infty & \infty & \infty & \infty \\ \infty & \infty & \infty & \infty \end{bmatrix} * \begin{bmatrix} \infty & 1 & 2 & \infty \\ \infty & \infty & 3 & 3 \\ \infty & \infty & \infty & 2 \\ \infty & \infty & \infty & \infty \end{bmatrix} = \begin{bmatrix} \infty & \infty & \infty & 6 \\ \infty & \infty & \infty & \infty \\ \infty & \infty & \infty & \infty \\ \infty & \infty & \infty & \infty \end{bmatrix}$

- $D_4 = (\infty)_{4\times4}$
- $P = D \oplus D^2 \oplus D^3 \oplus D^4$

$P = \begin{bmatrix} \infty & 1 & 2 & 4 \\ \infty & \infty & 3 & 3 \\ \infty & \infty & \infty & 2 \\ \infty & \infty & \infty & \infty \end{bmatrix}$

Find the shortest path from a to z.

- Dijkstra
- Matrix

![](img/c25dfd82fc242c2db53bc942dcad6885_1607_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1607_1.png)

## Remarks

- 我们一直在考虑的问题有许多重要的变体。在一种情况下，边可能具有表示距离、成本等的 *权重*。问题就是找到一条哈密顿回路（或路径），使得路径中权重的总和最小。例如，顶点可能代表城市，边代表交通线路；边的权重代表沿该边旅行的成本。这种版本的问题通常称为 *旅行商问题*。
