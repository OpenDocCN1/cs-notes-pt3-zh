
## 7.1 图的概念/Introduction of Graph

[定义]图
V是一个非空有限集，E是V上的一个二元关系，有序对（V，E）称为有向图/Directed Graph。
若将E中的有序对看成是无序的（即将e=(a,b)看成e={a,b}），则称（V，E）为无向图/Undirected Graph。有向图和无向图统称为图/Graph，记为G。
G = （V，E）

## [定义]顶点：
V 中的元素称为顶点，用带标记的点表示，也称为**结点/Vertices**。

## [定义]边：
在有向图G中，若e=（a，b）∈ E，e称为G的**有向边/directed edge**。用由 a 到 b 带箭头的线把a 和 b 连起来；
在无向图G中，若e=（a，b）∈ E，e称为G的**无向边/undirected edge**。a、b 间用连线连结，有向边和无向边统称为G的**边/edge**。

## [定义]图的分类
对图G=（V， E）。若对于任意的（a， b）∈ E， a ≠ b，则称图G为简单图/Simple Graph。

对图G=（V， E）。若允许E是一个重集，则称图G为重图/Multigraph。其相同的元素称为重边。

对图G=（V， E）。若G既允许是重图又允许是非简单图，则称图G为拟图/Pseudograph。

一般的G称为线性图/Linear Graph。

## 图的模型
- Niche Overlap Graphs in Ecology
- Influence Graphs
- Round-Robin Tournaments
- Precedence Graphs
- Traffic Map
- Family Graphs

## 7.2 图的术语/Graph Terminology

### [定义]相邻和关联：
在无向图G中，若e=（a，b）∈E，则称a与b相邻/adjacent，或边e关联a、b/incident或联结a、b/connect。a、b称为边e的端点或结束顶点/endpoint。

在有向图G中，若e=（a，b）∈E，即箭头由a到b，称a相邻到b，或a关联或联结b。a称为e的起点/initial vertex，b称为e的终点/terminal or end vertex。

### [定义] 孤立顶点：
若 a ∈ V，a 不与其他顶点相邻，称 a 为孤立顶点 isolated。

### [定义] 自回路：
若（a，a）∈ E，（{a，a}∈ E），称边（a，a）（{a，a}）是自回路/loop。

### 【定义】顶点的次：
在无向图G中，与a相邻的顶点的数目称为a的次数或度数/degree。记为deg(a)或d(a)。

在有向图G中，以a为终点的边的条数称为a的入次或入度/in-degree。记为deg⁻(a)或d⁻(a)。以a为起点的边的条数称为a的出次或出度/out-degree。记为deg⁺(a)或d⁺(a)。

## [定理1 (Handshaking)] 设无向图G= (V, E) 有e条边，则G中所有顶点的次之和等于e的两倍。
证明思路：利用数学归纳法。

## [定理2] 无向图中次为奇数的顶点个数恰有偶数个。
证明思路：将图中顶点的次分类，再利用定理1。

## [定理3] 设有向图G=（V， E）有e条边，则G中所有顶点的入次之和等于所有顶点的出次之和，也等于e。
证明思路：利用数学归纳法。

## 有向图与无向图的对应：
无向图对应有向图：加上箭头。
有向图对应无向图：去掉箭头。
称为underlying undirected graph

## 一些特殊的简单无向图：
- (1) Complete Graphs/完全图K<sub>n</sub>(n>0)
- (2) Cycles/环图C<sub>n</sub>(n>2)
- (3) Wheels/轮图W<sub>n</sub>(n>2)
- (4) n-Cubes/n-立方图Q<sub>n</sub>(n>0)
- (5) Bipartite Graphs/二分图
- Complete Bipartite Graphs/完全二分图Kn,m

## [定理4] 设无向完全图G有n个顶点，则G有n(n-1)/2条边。

## 一些特殊的其他图：
1. 有向完全图
2. 零图
3. 平凡图
4. 正则图：若图 $G=(V,E)$ 中每个顶点的次均为 $n$，称此图 $G$ 是 $n$-正则的 / $n$-regular。（PP455 T27）

## 【定义】子图：
$G=(V,E)$ 是图，若 $G'=(V',E')$ 也是图且满足：
1. $V'\subseteq V$；
2. $E'\subseteq E$；
则称 $G'$ 为 $G$ 的子图/subgraph。

注：
当 $V'=V$ 时，称 $G'$ 为 $G$ 的生成子图。
当 $E'\ne E$ 时，或 $V'\ne V$ 时称 $G'$ 为 $G$ 的真子图。

## [定义]补图/complementary graph :
G = (V， E) 是图， G’ = (V ’ ， E ’ ) 是G的子图， E ” = E − E ’ ， V ” =V−V’ 或是E ” 中边所关联的所有顶点集合，则G ” = (V ” ， E ” ) 称为G’ 关于G的相对补图。

## [定义]补图:
关于完全图的子图的补图称为此子图的绝对补图，若子图记为G，则补图记为 Ḡ 。

## Graphs/图论
![](img/5123c27d7478faaa822d0f1f02fc503f_1431_0.png)
![](img/5123c27d7478faaa822d0f1f02fc503f_1431_1.png)

图A是一个无向完全图
图B， C， D， E， F均是A的子图
图C的顶点 a 是孤立顶点
图B的边 [ a ， b ] 是孤立边
图D是图C的子图
图F是图D关于图C的余图
图E是图C的补图
（ A 是完全图， C 是A的子图 ）

## 练习
pp.443 6、7、11（a）
pp.454 17、20、27

## 7.3 图的表示与同构 / Representing Graph and Graph Isomorphism
图G表示的三种方法：
1. 集合表示
2. 邻接表（adjacency list）表示
3. 矩阵（matrix）表示
   1. 邻接矩阵（adjacency matrix）表示
   2. 关联矩阵（incidence matrix）表示

## Graphs/图论
【定义】邻接矩阵：
设有向图 $G=(V,E)$，$V=\{V_1,V_2,\cdots,V_n\}$，若用方阵 $A=(a_{ij})_{n\times n}$ 来表示，其中

$$a_{ij}=\begin{cases}1 & (V_i,V_j)\in E\\0 & (V_i,V_j)\notin E\end{cases}$$

称 $A$ 为 $G$ 的邻接矩阵。

## Graphs/图论
[定义]图的同构：
图 $G_1=(V_1,E_1)$，$G_2=(V_2,E_2)$，如果能建立 $V_1$ 与 $V_2$ 间的一一对应，在此对应下，$E_1$ 与 $E_2$ 中的边也一一对应，对有向图还保持关联方向的对应，则称图 $G_1$ 与 $G_2$ 同构/isomorphism，记作 $G_1\cong G_2$。

## 从图中不容易直接得出。
可用邻接矩阵，通过某种算法确定两个图是否同构。
上例的邻接矩阵：

\(\left[\begin{array}{ c c c c }
0 & 1 & 0 & 1 \\
0 & 0 & 0 & 1 \\
1 & 1 & 0 & 0 \\
0 & 0 & 1 & 0
\end{array}\right]\)

i

\(\left[\begin{array}{ c c c c }
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
1 & 0 & 0 & 1 \\
1 & 1 & 0 & 0
\end{array}\right]\)

ii
