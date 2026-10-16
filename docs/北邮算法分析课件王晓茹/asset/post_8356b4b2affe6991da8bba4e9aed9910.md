
## MST性质证明

![](img/18fa867d493fcce0c8a4a563c309db0a_489_0.png)

假设 G 的任何一棵最小生成树都不含边 \((u,v)\)。将边 \((u,v)\) 添加到 G 的一棵最小生成树 T 上，将产生含有边 \((u,v)\) 的圈，并且在这个圈上有一条不同于 \((u,v)\) 的边 \((u',v')\)，使得 \(u' \in U\)，\(v' \in V-U\)，如图所示。

将边 \((u',v')\) 删去，得到 G 的另一棵生成树 \(T'\)。由于 \(c[u][v] \le c[u'][v']\)，所以 \(T'\) 的耗费 \(\le\) T 的耗费。于是 \(T'\) 是一棵含有边 \((u,v)\) 的最小生成树，这与假设矛盾。

## Prim算法实质：最近顶点策略

### 2、Prim算法

设 \(G=(V,E)\) 是连通带权图，\(V=\{1,2,\dots,n\}\)。

构造 G 的最小生成树的 Prim 算法的基本思想是：首先置 \(S=\{1\}\)，然后，只要 S 是 V 的真子集，就作如下的贪心选择：选取满足条件 \(i \in S\)，\(j \in V-S\)，且 \(c[i][j]\) 最小的边，将顶点 j 添加到 S 中。这个过程一直进行到 \(S=V\) 时为止。

在这个过程中选取到的所有边恰好构成 G 的一棵最小生成树。

![](img/18fa867d493fcce0c8a4a563c309db0a_490_0.png)

### Prim算法取边的过程

![](img/18fa867d493fcce0c8a4a563c309db0a_491_0.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_491_1.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_491_2.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_491_3.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_491_4.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_491_5.png)

### 算法的复杂性分析

在上述 Prim 算法中，还应当考虑如何有效地找出满足条件 \(i \in S\)，\(j \in V-S\)，且权 \(c[i][j]\) 最小的边 \((i,j)\)。实现这个目的的较简单的办法是设置 2 个数组 `closest` 和 `lowcost`。

在 Prim 算法执行过程中，先找出 \(V-S\) 中使 `lowcost` 值最小的顶点 j，然后根据数组 `closest` 选取边 \((j, closest[j])\)，最后将 j 添加到 S 中，并对 `closest` 和 `lowcost` 作必要的修改。

用这个办法实现的 Prim 算法所需的计算时间为 \(O(n^2)\)。

## 3、Kruskal算法

Kruskal 算法构造 G 的最小生成树的基本思想是，首先将 G 的 n 个顶点看成 n 个孤立的连通分支。将所有的边按权从小到大排序。然后从第一条边开始，依边权递增的顺序查看每一条边，并按下述方法连接 2 个不同的连通分支：当查看到第 k 条边 \((v,w)\) 时，如果端点 v 和 w 分别是当前 2 个不同的连通分支 T1 和 T2 中的顶点时，就用边 \((v,w)\) 将 T1 和 T2 连接成一个连通分支，然后继续查看第 \(k+1\) 条边；如果端点 v 和 w 在当前的同一个连通分支中，就直接再查看第 \(k+1\) 条边。这个过程一直进行到只剩下一个连通分支时为止。

![](img/18fa867d493fcce0c8a4a563c309db0a_494_0.png)

## 思考题：Prim VS Kruskal 算法复杂性分析

关于集合的一些基本运算可用于实现 Kruskal 算法。

按权的递增顺序查看等价于对优先队列执行 `DeleteMin` 运算。可以用堆实现这个优先队列。

对一个由连通分支组成的集合不断进行修改，需要用到抽象数据类型并查集 `UnionFind` 所支持的基本运算。

当图的边数为 e 时，Kruskal 算法所需的计算时间是 \(O(e\log e)\)。当 \(e=\Omega(n^2)\) 时，Kruskal 算法比 Prim 算法差，但当 \(e=o(n^2)\) 时，Kruskal 算法却比 Prim 算法好得多。

## 贪心法的应用

### 计算机调度问题

### §1 Greedy Algorithms

**Note**

- Greedy algorithm works only if the local optimum is equal to the global optimum.
- Greedy algorithm does not guarantee optimal solutions. However, it generally produces solutions that are very close in value (heuristics) to the optimal, and hence is intuitively appealing when finding the optimal solution takes too much time.

### 1. A Simple Scheduling Problem

**The Single Processor Case**

Given \(N\) jobs \(j_1, j_2, \dots, j_N\), their running times \(t_1, t_2, \dots, t_N\), and one processor.

Schedule jobs to minimize the average completion time.
/* assume nonpreemptive scheduling 假定为非抢占式调度 */

**Example**

| job | j₁ | j₂ | j₃ | j₄ |
|-----|----|----|----|----|
| time | 15 | 8 | 3 | 10 |

**Schedule 1**

![](img/18fa867d493fcce0c8a4a563c309db0a_498_0.png)

**Schedule**

> Best scheduling is to make \(\{t_{i_k}\}\) nondecreasing（不减少，递增）.

**In general**

![](img/18fa867d493fcce0c8a4a563c309db0a_498_1.png)

\[
C = \sum_{k=1}^{N} (N-k+1)t_{i_k} = (N+1)\sum_{k=1}^{N} t_{i_k} - \sum_{k=1}^{N} k \cdot t_{i_k}
\]

### The Multiprocessor Case – N jobs on P processors

**Example**

P = 3

| job | j1 | j2 | j3 | j4 | j5 | j6 | j7 | j8 | j9 |
|---|---|---|---|---|---|---|---|---|---|
| time | 3 | 5 | 6 | 10 | 11 | 14 | 15 | 18 | 20 |

**An Optimal Solution**

![](img/18fa867d493fcce0c8a4a563c309db0a_499_0.png)

**Another Optimal Solution**

![](img/18fa867d493fcce0c8a4a563c309db0a_499_1.png)

### Minimizing the Final Completion Time

**An Optimal Solution**

![](img/18fa867d493fcce0c8a4a563c309db0a_499_2.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_499_3.png)

### 多机调度问题

多机调度问题要求给出一种作业调度方案，使所给的 n 个作业在尽可能短的时间内由 m 台机器加工处理完成。

约定：每个作业均可在任何一台机器上加工处理，但未完工前不允许中断处理。作业不能拆分成更小的子作业。

这个问题是 NP 完全问题，到目前为止还没有有效的解法。对于这一类问题，用贪心选择策略有时可以设计出较好的近似算法。

采用最长处理时间作业优先的贪心选择策略可以设计出解多机调度问题的较好的近似算法。

按此策略，当 \(n \le m\) 时，只要将机器 \(i\) 的 \([0, t_i]\) 时间区间分配给作业 \(i\) 即可，算法只需要 \(O(1)\) 时间。

当 \(n > m\) 时，首先将 n 个作业依其所需的处理时间从大到小排序。然后依此顺序将作业分配给空闲的处理机。算法所需的计算时间为 \(O(n\log n)\)。

例如，设 7 个独立作业 \(\{1,2,3,4,5,6,7\}\) 由 3 台机器 M1、M2 和 M3 加工处理。各作业所需的处理时间分别为 \(\{2,14,4,16,6,5,3\}\)。

按算法 `greedy` 产生的作业调度如下图所示，所需的加工时间为 17。

![](img/18fa867d493fcce0c8a4a563c309db0a_502_0.png)
