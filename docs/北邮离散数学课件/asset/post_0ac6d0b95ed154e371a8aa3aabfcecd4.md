
## FLEURY’s Algorithm

- *Step 3:* Repeat step 2 until no edges remains in *E*.

## Example

![](img/c25dfd82fc242c2db53bc942dcad6885_1507_0.png)

## Example

![](img/c25dfd82fc242c2db53bc942dcad6885_1508_0.png)

| Current Path | Next Edge | Reasoning |
|---|---|---|
| π: A | {A, B} | No edge from A is a bridge. Choose any one. |
| π: A, B | {B, C} | Only one edge from B remains. |
| π: A, B, C | {C, A} | No edge from C is a bridge. Choose any one. |
| π: A, B, C, A | {A, D} | No edge from A is a bridge. Choose any one. |
| π: A, B, C, A, D | {D, C} | Only one edge from D remains. |
| π: A, B, C, A, D, C | {C, E} | Only one edge from C remains. |
| π: A, B, C, A, D, C, E | {E, G} | No edge from E is a bridge. Choose any one. |
| π: A, B, C, A, D, C, E, G | {G, F} | {A, G} is a bridge. Choose {G, F} or {G, H}. |
| π: A, B, C, A, D, C, E, G, F | {F, E} | Only one edge from F remains. |
| π: A, B, C, A, D, C, E, G, F, E | {E, H} | Only one edge from E remains. |
| π: A, B, C, A, D, C, E, G, F, E, H | {H, G} | Only one edge from H remains. |
| π: A, B, C, A, D, C, E, G, F, E, H, G | {G, A} | Only one edge from G remains. |
| π: A, B, C, A, D, C, E, G, F, E, H, G, A |  |  |

## Example

![](img/c25dfd82fc242c2db53bc942dcad6885_1509_0.png)

## Euler Paths and Circuits

- Definition
- Existence theorems
- Produce an Euler circuit –Fleury’ Algorithm

## [定理1]（欧拉定理）：

没有次为 0 的孤立顶点的无向图存在欧拉道路的充要条件是：

- (1) 图是连通的；
- (2) 图中奇次顶点个数是 0 个或 2 个。

## 证明：

## 必要性：

若存在欧拉道路，且没有 0 次顶点，则每个顶点都有边关联，而边又全在欧拉道路上，故所有顶点都连通。

除了起点，终点外，欧拉道路每经过一个顶点，使顶点的次增加 2，故只有起点和终点才可能成为奇次顶点，而一个奇次顶点是不可能的，当无奇次顶点时，是欧拉回路。

## 充分性：

若(1)，(2)成立, 构造欧拉道路.

若图G存在奇次顶点，任取一个作为起点，若不存在，则任取一个顶点作为起点。

若此图有 n 条边，总次为 2 n。每进入或离开一个顶点，让此顶点的次减 1，由于除了两个（或没有）奇次顶点外，其余顶点次为偶数，只要进得去，一定出得来，直至进入另一个奇次顶点（或起点）作为终点。这样构造的是简单道路，如果经过所有的边，即得到一条欧拉道路。

不然，记走过的简单道路为 p₁， p₁上顶点集 V₁，边集 E₁， G₁ =（V₁， E₁）是G的子图。

若 G₂ = (V₂, E₂) 是 G₁ 的关于 G 的余图，E₂ = E − E₁，但 V₁ ∩ V₂ ≠ φ，否则 G 不连通，设 C ∈ V₁ ∩ V₂，从 C 出发，用上面方法作 G₂ 的简单回路 p₂ 回到 C，这能做到。

因为作好 p₁ 后，留下顶点的次都是偶次。若 p₁ ∪ p₂ 经过所有边，则欧拉道路是 p₁ 走到 C 时，先把 p₂ 走完，最后走完 p₁ 的余下道路。

若 p₁ ∪ p₂ 仍未经过所有边，将 p₁ ∪ p₂ 视为 p₁ 重复上述过程，由于 E 边有限，故存在欧拉道路。

例1：

![](img/c25dfd82fc242c2db53bc942dcad6885_1515_0.png)

（1）顶点的次： A(3), B(2), C(4), D(2), E(6), F(2), G(6), H(2), I(4), J(3)。其中奇次顶点A， J

（2）从A出发，走一条道路

（A,C,E,A,B,C,D,E,G,J）

(3) G₁ = (V₁, E₁)
V₁ = {A, B, C, D, E, G, J}
E₁ = { (A, B), (B, C), (A, C), (C, D), (C, E), (D, E), (E, G), (G, J) }

G₂ = (V₂, E₂)
E₂ = { (E, F), (F, G), (E, J), (G, H), (G, I), (I, J), (H, I) }
V₂ = {E, F, G, H, I, J}

E ∈ (V₁ ∩ V₂)

（4）从E出发回到E的回路（E，F，G，I，J，E），加入到P₁中
P₁′ = （A，C，E，F，G，I，J，E，A，B，C，D，G，J）
（5）还有未经过的边，重复上述过程，从G出发，（G，H，I，G），再加入即得欧拉道路。

## Hamiltonian Paths and Circuits（哈密顿路径与回路）

## Hamilton(哈密顿)道路问题：

1859年发明的一种游戏。
在一个实心的正十二面体，20个顶点标上世界著名大城市的名字，要求游戏者从某一城市出发，遍历各城市一次，最后回到原地。

这就是“绕行世界”问题。即找一条经过所有顶点（城市）的基本道路（回路）。

## Round-the-World Puzzle

- Can we traverse all the vertices of a dodecahedron, visiting each once?

![](img/c25dfd82fc242c2db53bc942dcad6885_1520_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1520_1.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_1520_2.png)

## [定义]哈密顿道路/回路：

G = (V, E)，G中经过V中所有顶点的基本道路称为哈密顿道路/Hamilton Path，简称H道路。

G = (V, E)，G中经过V中所有顶点的基本回路称为哈密顿回路/Hamilton Circuit，简称H回路。

## Hamiltonian Graph （哈密顿图）

- A graph has a *Hamiltonian tour* if there is a tour that visits every vertex exactly once (and returns to its starting point).
- A graph with a Hamiltonian tour is called a *Hamiltonian graph*.
- A *Hamiltonian path* is a path that contains each vertex exactly once.

汉密顿通路（回路）

经过图中每个结点一次且仅一次的通路(回路)。

汉密顿图

存在汉密顿回路的图。

G'

## Is it Hamiltonian?

- A graph of the vertices of a dodecahedron.

![](img/c25dfd82fc242c2db53bc942dcad6885_1525_0.png)

Yes.

## Euler tour
Hamiltonian tour

- Left one has a Hamiltonian path, but not a Hamiltonian tour.

![](img/c25dfd82fc242c2db53bc942dcad6885_1526_0.png)

- Right one has an Euler tour, but no Hamiltonian tour.
