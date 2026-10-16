
由于平面图的区域比较难数（如果已能画成边不相交的图，则已明确是平面图了），对一些特殊的图，欧拉公式有以下推论。

## 推论一

如果 $G = (V, E)$ 是连通的平面简单图且 $v \ge 3$，则有 $e \le 3v - 6$。

## 推论二

如果图 $G = (V, E)$ 是连通的平面简单图且 $v \ge 3$，每个区域至少由四边围成，则有 $e \le 2v - 4$。

用推论 1 和推论 2 易证明三管道图 $K_{3,3}$ 及 5 个顶点完全图 $K_5$ 一定不是平面图。

三管道图，每个区域都由 4 条边围成，$v = 6$，$e = 9$，$2v - 4 = 12 - 4 = 8 < 9 = e$。

$K_5$ 每个区域至少由三条边围成，$v = 5$，$e = 10$，$3v - 6 = 15 - 6 = 9 < 10 = e$。

## Proof

- By induction on the number of cycles of $G$。
- **Base case:** $G$ has no cycles.
- $G$ is connected, so it must be a tree.
- Thus $e = v - 1$ and $f = 1$。

$$
v - e + f = v - (v - 1) + 1 = 1 + 1 = 2
$$

### Inductive step

- Suppose $G$ has at least one cycle $C$ containing edge $e$.
- Let $G' = G - e$。

![](img/c25dfd82fc242c2db53bc942dcad6885_1639_0.png)

- $G'$ is connected since $e$ was on a cycle.
  - $f' = f - 1$ and $G'$ has fewer cycles than $G$。
  - $v' = v$。
  - $e' = e - 1$。
- By induction hypothesis:

$$
v' - e' + f' = 2
$$

$$
v - (e - 1) + (f - 1) = 2
$$

$$
v - e + f = 2
$$

## Corollary

- No matter how we redraw a plane graph, it will have the same number of faces.
- **Proof:** $f = 2 - v + e$ is determined by $v$ and $e$, neither of which changes when we redraw the graph.

## Theorem

- Every (simple) *n*-node planar graph *G* has at most $3n - 6$ edges。

### Corollary

- If *G* is a connected planar simple graph, then *G* has a vertex of degree not exceeding five.

### Proof

- $n = 3$: clearly true.
- $n \ge 3$: consider a graph $G$ with a maximal number of edges.
- $G$ must be connected, or else we could add an edge.
- Thus $n - e + f = 2$。
- Every face has at least 3 edges on its boundary.
- Every edge lies on the boundary of at most 2 faces.
- Thus $2e \ge 3f$。

$$
n - e + f = 2
$$

$$
3n - 3e + 3f = 6
$$

$$
3n - 3e + 2e \ge 6
$$

$$
e \le 3n - 6
$$

![](img/c25dfd82fc242c2db53bc942dcad6885_1646_0.png)

$e \le 3v - 6$ 为简单连通平面图的必要条件。

$K_5$ 不是平面图。

![](img/c25dfd82fc242c2db53bc942dcad6885_1647_0.png)

$K_{3,3}$

$9 \le 3 \times 6 - 6 = 12$

$e \le 3v - 6$

但 $K_{3,3}$ 不是平面图。

虽然欧拉公式可用来判定一个图不是平面图，但是还没有一个简便的方法来确定一个图是平面图。在给定图 $G$ 的边上，插入一个二度结点，使一边分成两边，或者对于关联于一个 2 度结点的两边，去掉该结点，使两边变成一边，这些都不影响图的平面性。

## 同胚

给定两个图 $G_1$ 和 $G_2$，如果它们同构，或者通过反复插入或去掉 2 度结点后，$G_1$ 和 $G_2$ 同构，则称 $G_1$ 和 $G_2$ 是 2 度结点内同构的，也称 $G_1$ 和 $G_2$ 是同胚的。

## 库拉托夫斯基定理

一个图是平面图的充分必要条件是它不含与 $K_5$ 或 $K_{3,3}$ 在 2 度结点内同构的子图。

![](img/c25dfd82fc242c2db53bc942dcad6885_1650_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1650_1.png)

## The Kuratowski Graphs

$K_{3,3}$

![](img/c25dfd82fc242c2db53bc942dcad6885_1651_0.png)

$K_5$

![](img/c25dfd82fc242c2db53bc942dcad6885_1651_1.png)

## $K_{3,3}$ is not planar either

- When we redraw $K_{3,3}$, the blue cycle will be laid out

![](img/c25dfd82fc242c2db53bc942dcad6885_1653_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1653_1.png)

## Insight 1

- If we replace edges in a Kuratowski graph by paths of whatever length, they remain non-planar.

![](img/c25dfd82fc242c2db53bc942dcad6885_1654_0.png)

## Insight 2

- If a graph $G$ contains a subgraph obtained by starting with $K_5$ or $K_{3,3}$ and replacing edges with paths, then $G$ is non-planar.

![](img/c25dfd82fc242c2db53bc942dcad6885_1655_0.png)

## Kuratowski’s Theorem [1930]

- A graph is planar if and only if it contains no subgraph obtainable from $K_5$ or $K_{3,3}$ by replacing edges with paths.

## 对偶图

给定平面图 $G = (V, E)$，$F_1, F_2, \ldots, F_r$ 为 $G$ 的面。如果存在图 $G^* = (V^*, E^*)$ 满足：

- (1) 对于图 $G$ 的任意一个面 $F_i$，内部仅取一点 $v_i^* \in V^*$；
- (2) 若图 $G$ 的面 $F_i$ 与 $F_j$ 有公共边，作边 $e_k^* \in E^*$，使 $e_k^* = (v_i^*, v_j^*)$ 且与 $e_k$ 相交；
- (3) 当且仅当 $e_k$ 只是面 $F_i$ 的边界时，$v_i^*$ 存在一个环 $e_k^*$ 与 $e_k$ 相交。

则称图 $G^*$ 是 $G$ 的对偶图。

![](img/c25dfd82fc242c2db53bc942dcad6885_1658_0.png)

## 自对偶图

如果平面图 $G$ 的对偶图 $G^*$ 同构于 $G$，则称 $G$ 为自对偶图。

![](img/c25dfd82fc242c2db53bc942dcad6885_1659_0.png)
