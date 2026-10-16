

## 6.1.3 图的表示

三种最常用的表示方法：

- 1. 邻接矩阵
- 2. 邻接表
- 3. 邻接多重表

实际选择取决于应用。

### 6.1.3.1 邻接矩阵

G 的邻接矩阵是一个 n×n 的数组，记为 a，使得：

$$a[i,j]=\begin{cases}1 & \text{iff }(i,j)\in E(G)\text{ (or }\langle i,j\rangle\in E(G)\text{)}\\0 & \text{otherwise}\end{cases}$$

下一张幻灯片展示了 G₁、G₃ 和 G₄ 的邻接矩阵。

![](img/15e8d7d94d8ddf02cb6839870195a31e_460_0.png)

![](img/15e8d7d94d8ddf02cb6839870195a31e_460_1.png)

|  | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| 1 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| 2 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| 3 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| 4 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| 5 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 |
| 6 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| 7 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |

# $G_4$

对于一个图，a 是对称的，且

dᵢ = Σⱼ₌₀ⁿ⁻¹ a[i][j]

对于有向图，a 可能不对称，且

out-dᵢ = Σⱼ₌₀ⁿ⁻¹ a[i][j]

in-dⱼ = Σᵢ₌₀ⁿ⁻¹ a[i][j]

### 问题：G 中有多少条边？

使用 a，我们需要 O(n²)。当 e << n² /2 时，如果我们仅显式表示 G 中的边，则可以以 O(e + n) 的时间解决上述问题。

由此得到：

### 6.1.3.2 邻接表

- 邻接矩阵的 n 行表示为 n 条链。
- 链 i 中的节点表示从 i 相邻的顶点。

![](img/15e8d7d94d8ddf02cb6839870195a31e_464_0.png)

- 链节点的 **data** 字段存储相邻顶点的索引。
- 每个链中的顶点不要求有序。
- 一个数组 **adjLists** 用于以 O(1) 访问任意链。

```
class LinkedGraph
{
public:
    LinkedGraph (const int vertices): e(0)
    {
        if (vertices < 1) throw "Number of vertices must be > 0";
        n = vertices;
        adjLists = new Chain<int>[n];
        Chain<int> c; // set c.first to 0
        fill(adjLists, adjLists+n,c);
    };
private:
    Chain<int>* adjLists;
    int n;
    int e;
};
```

# adjLists

# data link

[0]

[1]

[2]

[3]

(a) G₁

[0]

[1]

[2]

(b) G₃

# adjLists

![](img/15e8d7d94d8ddf02cb6839870195a31e_468_0.png)

(c) G₄

对于一个具有 n 个顶点和 e 条边的无向图，该表示需要一个大小为 n 的数组和 2e 个链节点。

现在可以在 O(e+n) 时间内确定 G 中边的总数。

对于有向图，顶点的入度确定起来稍复杂一些 --- 使用一个向量 c[n]，当从 i 遍历到 j 时，c[j]++。

### 逆邻接表：

- 每个顶点一个列表
- 列表 i 中的节点表示与顶点 i 相邻的顶点。

以下是 G₃ 的逆邻接表：

| Vertex | Inverse adjacency list |
|---|---|
| [0] | 1 0 |
| [1] | 0 0 |
| [2] | 1 0 |

![](img/15e8d7d94d8ddf02cb6839870195a31e_470_0.png)

![](img/15e8d7d94d8ddf02cb6839870195a31e_470_1.png)

### 将邻接表和逆邻接表的节点结合起来形成正交表节点：

| tail | head | column link | row link |
|---|---|---|---|

以下是 G₃ 的正交表示：

![](img/15e8d7d94d8ddf02cb6839870195a31e_471_0.png)

### 6.1.3.3 邻接多重表

在无向图的邻接表中，每个 (u, v) 由 2 个条目表示。

在某些情况下，有必要能够确定特定边的第二个条目并将该边标记为已使用。

因此我们需要多重表：每个边恰好有一个节点，但它在两个列表中。

| m | vertex1 | vertex2 | path1 | path2 |

注意一条边可以从 path1 或 path2 标记。

```
class MGraph;
class MGraphEdge {
friend MGraph;
private:
    bool m;
    int vertex1, vertex2;
    MGraphEdge *path1, *path2;
};
typedef MGraphEdge *EdgePtr ;
class MGraph {
public:
    MGraph(const int);
private:
    EdgePtr *adjMultiLists;
    int n;
    int e;
};
```

