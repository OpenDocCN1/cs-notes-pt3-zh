

## Floyd-Warshall 算法

![](img/a8f1b433a70f1e5c410c8b43e41b650e_750_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_751_0.png)

|   | s | t | x | y | z |
|---|---:|---:|---:|---:|---:|
| s | 0 | 8 | 9 | 5 | 7 |
| t | 6 | 0 | 1 | 2 | 4 |
| x | 6 | 14 | 0 | 11 | 4 |
| y | 4 | 3 | 4 | 0 | 2 |
| z | 2 | 10 | 6 | 7 | 0 |

可能经过 s、t、x、y 的从 u 到 v 的最短路径

![](img/a8f1b433a70f1e5c410c8b43e41b650e_752_0.png)

## 路线图

- 最小生成树
- 如何设计贪心算法
  - 找零问题
  - 活动选择问题
  - 哈夫曼编码
  - 背包问题

## MST

给定一个带正边权的无向图 G（连通）。

**定义.** G 的生成树是连通且无环的子图 T。

![](img/a8f1b433a70f1e5c410c8b43e41b650e_756_0.png)

不连通

![](img/a8f1b433a70f1e5c410c8b43e41b650e_756_1.png)

不无环

## 最小生成树

**问题：** MinSpanning
**输入：** 一个连通无向图 G = (V, E)，其中每条边都有加权长度
**输出：** G 的成本最小的生成树

![](img/a8f1b433a70f1e5c410c8b43e41b650e_757_0.png)

## 割性质

![](img/a8f1b433a70f1e5c410c8b43e41b650e_758_0.png)

**定义：割**
割 {S, T} 是顶点集 V 的一个划分为两个子集 S 和 T。

**定理（割性质）** 给定任意割，跨越该割的最小权重的边在某个 MST 中。

## Kruskal 算法

(h, g), (c, i), (g, f), (a, b), (c, f), (c, d), (i, g), (i, h), (b, c), (a, h), (d, e), (e, f), (b, h)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_759_0.png)

### 算法 8.3 Kruskal

```text
Input: A weighted connected undirected graph G = (V, E) with n vertices.
Output: The set of the edges T of a minimum cost spanning tree for G.

1. Sort the edges in E by nondecreasing weight.
2. for each vertex v ∈ V do Makeset({v}) end for
3. T = {}
4. while |T| < n − 1
5.   Let (x, y) be the next edge in E
6.   if Find(x) ≠ Find(y) then
7.     Add(x, y) to T
8.     Union(x, y)
9.   end if
10. end while
```

## Prim 算法

![](img/a8f1b433a70f1e5c410c8b43e41b650e_761_0.png)

### 算法 8.4 Prim

```text
Input: A weighted connected undirected graph G = (V, E), where V = {1, 2, …, n}.
Output: The set of edges T of minimum cost spanning tree for G.

1. T ← {}; X ← {1}; Y ← V \ {1}
2. for y ← 2 to n
3.   if y is adjacent to 1 then
4.     N[y] ← 1
5.     C[y] ← c[1, y]
6.   else C[y] ← ∞
7.   end if
8. end for
9. for j ← 1 to n − 1
10.   Let y be such that C[y] is minimum
11.   T ← T ∪ {(y, N[y])}
12.   X ← X ∪ {y}
13.   Y ← Y \ {y}
14.   for each edge (y, w) such that w ∈ Y
15.     if c[y, w] < C[w] then
16.       N[w] ← y
17.       C[w] ← c[y, w]
18.     end if
19.   end for
20. end for
```

Θ(n²)

Heap: Θ(m log n)

## 稠密图

- dense: $m = n^{1+\varepsilon}$, $\varepsilon$ is not too small.
- d-heap, $d = m/n$
- complexity: $O(nd\log_d n + m\log_d n) = O(m)$

## 比较

| 算法 | 一般情况 | 稠密 |
|---|---:|---:|
| Prim | O(m log n) | O(m) |
| Kruskal | O(m log m) | O(m log m) |
| Dijkstra | O(m log n) | O(m) |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_765_0.png)

Kruskal 演示

![](img/a8f1b433a70f1e5c410c8b43e41b650e_765_1.png)

Prim 演示

## 正确性

**定理（GeneralMSTAlgorithm）**
设 A 是包含在 G 的某个 MST 中的 E 的子集，设 {S, V − S} 是尊重 A 的 G 的任意割，且 (u, v) 是跨越 S、V − S 的最轻边。
则 A ∪ {(u, v)} 包含在某个 MST 中。

**定理**
Kruskal 算法和 Prim 算法能正确找到最小成本生成树。

