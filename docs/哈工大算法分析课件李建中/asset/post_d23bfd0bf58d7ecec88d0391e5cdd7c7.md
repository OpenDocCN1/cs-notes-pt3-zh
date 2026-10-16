
![](img/9e822ee25d7fb44c33253ed3ff372fc1_63_0.png)

## Greedy算法 (Q为min-heap, 见黑皮书)

```
Huffman(C, F)
1. n ← |C|; Q ← 根据F构造C; T为一个空树;
2. FOR i ← 1 To n-1 Do
3. z ← Allocate-Node();
4. left[z] ← x ← Extract-min(Q) /* 从Q删除x */;
5. right[z] ← y ← Extract-min(Q) /* 从Q删除y */;
6. f(z) ← f(x)+f(y);
7. Insert(Q, z, f(z));
8. Return Extract-min(Q) /* 返回树根 */
```

## 复杂度分析

- 第1步: O(nlogn)
- 每次循环: O(logn), 循环n-1次: O(nlogn)
- T(n)=O(nlogn)

## 正确性证明

定理3. Huffman算法产生一个优化前缀编码树
证. 由于发现1和发现2成立, 而且Huffman算法是处理第2种Greedy编码问题时构造树时进行局部优化选择, 所以Huffman算法产生一个优化前缀编码树。

## 6.4 Minimal spanning tree problem

- 问题定义
- 设计贪心算法
- 优化解结构分析
- Greedy算法性质
- Kruskal算法
- 算法复杂性

## 问题的定义

定义
设G=(V,E)是一个连通和加权图, G的生成树是指一个子图T=(V,E'), E'⊆E.
设W: E→R+是边的权值函数, 则T的权值定义为W(T)=Σ_{e∈E'} W(u,v).
最小生成树
G的最小生成树是指W(T)最小的G的子树.
问题定义
输入: 无向连通图G=(V,E), 及其权W
输出: G的最小生成树

![](img/9e822ee25d7fb44c33253ed3ff372fc1_64_0.png)

## 案例

## 基本思想

## 设计核心算法方法

每次从一个最小权重的边 (u, v) 开始，u 和 v 分别属于两个不同的集合，则把 (u, v) 加入到最小生成树中，否则丢弃 (u, v)。

- 初始：A=空；构造森林 G_A=(V, A)；
- 循环：从森林 G_A 中选择权值最小的边 (u, v) 加入 A，直至 A 所含边数达到 n-1。

![](img/9e822ee25d7fb44c33253ed3ff372fc1_64_1.png)

## 一类普适的定义

Generic-MST(G, W)
1. A=∅;
2. While A 不是连通的 Do
3.  寻找一个最小权重的边 (u, v);
2.  A=A∪{(u, v)};
3. Return A

## 贪心算法

- 贪心选择：从图中选择一最小权重的边直接构成树的一棵分支，直至构成一棵树
- 剩余问题继续构造。

![](img/9e822ee25d7fb44c33253ed3ff372fc1_64_2.png)

## 优化解的结构分析

定理1. 设 T 是 G 唯一的最小生成树，而 T 也含有 T1 和 T2，T 是 G 的子图或 G 的生成树，则 T 是 G 的最小生成树，而 T1 是 G1 的最小生成树，T2 是 G2 的最小生成树。证。

![](img/9e822ee25d7fb44c33253ed3ff372fc1_64_3.png)

## Greedy算法

- 定义1. 若图 G=(V, E) 有一个割 (S, V-S)
- 定义2. 若 u∈S, v∈V-S, 则 (u, v) 被称作割 (S, V-S) 的一条边。
- 定义3. 若割 (S, V-S) 的一条边 (u, v) 权重最小，则 (u, v) 被称作割 (S, V-S) 的最小边，
  则该边 (S, V-S) 属于 A。
- 定义4. 若 (S, V-S) 的最小边 (u, v) 被称作该割所含所有 (S, V-S) 的最小边，则 (u, v) 属于 A。

![](img/9e822ee25d7fb44c33253ed3ff372fc1_64_4.png)

## 算法正确性

定理2. MST-Kruskal(G, W)算法就能够产生图 G的最小生成树。

证. 因为算法就象Greedy算法那样按后 顺序也这样，并且每次选择的都是 最小边。

## 6.5 Theoretical foundations of Greedy Algorithms

- Matroid (拟阵)
- Matroid 例子
- Matroid 性质
- 加权Matroid上的Greedy算法
- 算法正确性

## Matroid (拟阵)

- Matroid定义

Matroid是一个对偶为M=(S, I), 满足：
(1) S是一个有限集合。
(2) I是S的子集族的集合, I中的集合称为 S的独立子集。
(3) 继承性: 若A∈I, B⊆A, 则B∈I
(4) 交换性: 若A∈I, B∈I, |A|<|B|, 则 ∃e∈B-A使A∪{e}∈I。

## 实例(Graphic Matroid)

- 实例1.

设G=(V, E)是一个无向图, 由G定义的 M_G=(S_G, I_G)定义如下: S_G是G的边集合E, I_G={A | A⊆E, G(V, A)是森林}。

- 实例2.

设G是一个无向图, 则M_G=(S_G, I_G)是一个Matroid。

注. ① S_G=E是一个有限集合。
② ∀e∈E, G_A(V, {e})是一个集合, {e}∈I_G。
于是, I_G是S_G的非空集。

① M_G满足继承性:
若A∈I_G, B⊆A, 则G_A(V, B)是一个树, 于是 A∈I_G, M_G满足继承性。

② M_G满足交换性:
若A∈I_G, B∈I_G, |A|<|B|。
假设存在, 则G_A(V, A)与G_B(V, B)树。
G_A=(V, A)与G_B=(V, B)树有|V|-|A|与|V|-|B|条树。
由|V|-|A|>|V|-|B|, G_A有更多树T, T的顶点构成G_A的无环树。
由T来遍历, T也包含(u, v), 若G_A无环树, 于是(V, A∪{(u,v)})是森林, A∪{(u,v)}∈I_G, (u,v)∈B-A, M_G满足交换性。

## Matroid性质

- 定理2. M=(S, I)是一个Matroid, A∈I, 若A∪{e}∈I, x∈A, x换为A的一个extension.

- 定理3. 设M=(S, I)是Matroid, A∈I, 若A没有extension, 则A是最大独立子集。

- 定理2. 一个Matroid的两个最大独立子集具有相同大小。

设A是Matroid M的最大独立子集, 而B是 M的一个独立子集, |A|≤|B|。
根据M的交换性, ∃e∈B-A使A∪{e}∈I, 与A最大矛盾。

## 加权Matroid上Greedy 算法
Matroid的优化问题
实例背景：
据已有用Greedy算法能解决的最小生成树问题可推广到加权Matroid中寻找优化问题。给定Matroid M=(S,I)及其中权重W，我们按某种顺序A∈I，使得W(A)最大。

## 实例/最大生成树问题
一问题定义
输入：无向图G=(V,E)，权重函数W:E→正整数集
输出：边集A⊆E，G(V,A)是森林，W(A)最大
一最大生成树加权Matroid上优化问题
一构造：
M₀=(S₀,I₀), S₀=E, I₀={A⊆E, G(V,A)是森林}，M₀是森林
M₀的权重函数W₀：
W(A)最大

## 实例2：最小生成树问题
一问题定义
输入：无向图G=(V,E)，权重函数W:E→正整数集
输出：边集A⊆E，G(V,A)是森林，W(A)最小
一最小生成树加权Matroid上优化问题
构造：
M₀=(S₀,I₀), S₀=E, I₀={A⊆E, G(V,A)是森林}，M₀是森林
构造权重函数W₀：
W₀(x)=W(x), W₀≥max{W(x)}
W₀(A)=W(A)
W₀(A)=W(A), ∀x∈E
M₀被赋予W(A)最小：
(V,A)连通
W(A)最小, 有|V|-1条边。

## 加权Matroid优化问题的定义
输入：Matroid M=(S,I)，权重W:S→正整数集
输出：M的独立集A∈I，使得W(A)最大

## 算法
Greedy(M,W)
1 A=Φ;
2 按W值递减排序S;
3 For ∀x∈S (按W(x)递减顺序) DO
4 If A∪{x}∈I /* 保持者W(x)最大取x */
5 Then A=A∪{x};
6 Return A.
时间复杂
step 2: O(|S|log|S|)
step 4: O(f(|S|))
T(|S|)=O(|S|log|S|+|S|f(|S|))

## 优化性质
定义1: 设x是一个被Greedy算法中丢弃元素，也含x的集合A是A包含可换成M'=(S',I')的独立集S'=A-{x}, M'=(S',I')定义如下：
I'={B⊆S' | B∪{x}∈I}
则M'的每个独立集M的独立集构成一个组。
证：因为A-{x}∈I, 称A-{x}∈I'。
A' =A∪M'的独立集，则M'的每个独立集B满足W(B)>W(A')。
由子B∪{x}∈I, W(A)=W(A')+W(x),
W(B∪{x})=W(B)+W(x)>W(A')+W(x)=W(A),
故A优化错误。
