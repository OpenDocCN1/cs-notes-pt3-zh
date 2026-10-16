
![](img/9e822ee25d7fb44c33253ed3ff372fc1_112_0.png)

## 集合覆盖问题：LP-随机舍入算法

- LP-随机舍入算法
  1. 通过求解 LP 松弛问题得到解 \(x^*\)，满足 \(\sum_{S\ni e}x_S\ge 1\)；
  2. \(C=\emptyset\)；
  3. 对每个 \(S\in\mathcal S\)：生成随机数 \(\mathrm{rand}\)，若 \(\mathrm{rand}>1-x_S\)，则 \(C=C\cup\{S\}\)；/* \(S\) 以概率 \(x_S\) 被选中 */
  4. 输出 \(C\)。

**定理 7.** 对于集合覆盖的 LP-随机舍入算法，每个集合以概率 \(x_S\) 被选入 \(C\)，因此其期望成本等于 LP 最优值：
\[
\mathbb E[\mathrm{cost}(C)]=\sum_{S\in\mathcal S}\Pr[S\text{ 被选入 }C]\,c(S)=\sum_{S\in\mathcal S}x_S c(S)=\mathrm{OPT}_{LP}.
\]

**定理 8.** 对于集合覆盖的 LP-随机舍入算法，\(\forall e\in U\)，\(e\) 被覆盖的概率至少 \(1-1/e\)。

证明：设包含 \(e\) 的集合为 \(S_1,\dots,S_k\)，令 \(x_i=x_{S_i}\)。由于 \(\sum_{i=1}^k x_i\ge 1\)，
\[
\Pr[e\text{ 未被覆盖}]=\prod_{i=1}^k(1-x_i)
\le \left(1-\frac{\sum_{i=1}^k x_i}{k}\right)^k
\le \left(1-\frac1k\right)^k
\le \frac1e.
\]
因此 \(\Pr[e\text{ 被覆盖}]\ge 1-\frac1e\)。

## Primal-dual schema

- 集合覆盖的 Primal-dual Schema 算法
  1. \(x_S=0\)；/* 对每个集合 \(S\in\mathcal S\) 有一个变量 \(x_S\) */
  2. \(y_e=0\)；/* 对每个元素 \(e\in U\) 有一个变量 \(y_e\) */
  3. \(F=\emptyset\)；/* \(F\) 为已覆盖元素的集合 */
  4. while \(F\neq U\) do
     - 取 \(e\in U\setminus F\)；
     - 增大 \(y_e\)，直到存在某个 \(S\in\mathcal S\)（\(e\in S\)）满足 \(\sum_{e'\in S}y_{e'}=c(S)\)；
     - 将上一步中满足 \(\sum_{e'\in S}y_{e'}=c(S)\) 的集合 \(S\) 选中：\(x_S=1\)，\(F=F\cup S\)；
  5. 输出所有满足 \(x_S=1\) 的集合 \(S\)。

**引理 2.** 在上述算法中，while 循环结束后，\(x_S\) 是原始可行解，\(y_e\) 是对偶可行解。

**引理 3.** 上述算法中，while 循环结束后，\(x_S\) 与 \(y_e\) 满足如下两个条件：

1. 对 \(\forall S\in\mathcal S\)，\(x_S>0\Rightarrow \sum_{e\in S}y_e=c(S)\)；
2. 对 \(\forall e\in U\)，\(y_e>0\Rightarrow 1\le \sum_{S\ni e}x_S\le f\)，其中 \(f=\max_{e\in U}|\{S\in\mathcal S:e\in S\}|\) 是元素被集合覆盖的最大频率。

**定理 9.** 若在 primal-dual schema 的增量过程中，变量 \(x,y\) 满足上述两个条件，则其增量系数为 \((\alpha,\beta)=(1,f)\)。

证明：由引理 3，执行增量过程后，其对应变量 \(x,y\) 满足上面两个条件；这两种情况对应增量系数 \((\alpha=1,\beta=f)\)。由定理 4，
\[
\mathrm{cost}(C)=\sum_{S\in\mathcal S}x_S c(S)
=\sum_{e\in U}y_e\left(\sum_{S\ni e}x_S\right)
\le f\sum_{e\in U}y_e.
\]
又由 \(y\) 的对偶可行性，\(\sum_{e\in U}y_e\le \mathrm{OPT}_{LP}\)，因此取得增量系数 \((\alpha=1,\beta=f)\)。其过程与此类似，具体细节略。

## 1. SONET 电话负载问题

输入：含有 \(n\) 个顶点的环（其中所有顶点按照顺时针方向排列为 \(0,1,2,\dots,n-1\)）。一个电话呼叫集合 \(C\)，其中 \((i,j)\in C\) 表示节点 \(i\) 呼叫节点 \(j\)。任意电话的路由既可以按照顺时针方向进行，也可以按照逆时针方向进行。对 \(C\) 中电话的路由策略，边 \((i,i+1\bmod n)\) 的负载为通过该边的电话个数 \(L_i\)。环的总负载为 \(\max_{1\le i\le n}L_i\)。

输出：\(C\) 中电话的一个路由策略，使得环的总负载最小。

问题：设计一个 2-近似算法求解 SONET 电话负载问题。

## 2. 匹配问题

Consider the maximum weight matching problem in a (non-bipartite) graph \(G=(V,E)\). More precisely, given a non-negative weight \(w_{ij}\) for every edge \((i,j)\in E\), the problem is to find a matching of maximum total weight.

Consider the following greedy algorithm: start from an empty matching and repeatedly add an edge of maximum weight among all edges which do not meet any of the edges chosen previously. Stop as soon as the matching is maximal (i.e., no other edge can be added). Let \(M_G\) denote the greedy matching and \(Z_G\) its cost. In this problem you are asked to show that the greedy algorithm is a 2-approximation algorithm.

- (a) Show that the following linear program gives an upper bound \(Z_{up}\) on the optimal value \(Z_{opt}\) of the maximum weight matching problem:
\[
\begin{aligned}
\min\quad & \sum_{i\in V}x_i\\
\text{s.t.}\quad & x_i+x_j\ge w_{ij},\quad \forall (i,j)\in E,\\
& x_i\ge 0,\quad \forall i\in V.
\end{aligned}
\]

- (b) From the greedy matching \(M_G\), construct a feasible solution \(x\) to the above linear program and show that its value is \(2Z_G\). Conclude that \(2Z_G\ge Z_{opt}\).

## 3. 装箱问题

输入：长度为 \(C\) 的箱子（数量不限），长度分别为 \(0\le w_1,w_2,\dots,w_n\le C\) 的 \(n\) 个不可分割的物品。

输出：物品的装箱策略，使得所用箱子的个数最少。

### First-Fit 算法

依次考察每个物品。对于当前物品 \(i\)，在以前用过的箱子 \(B_1,\dots,B_k\) 中找到下标最小的能够容纳 \(i\) 的箱子，将物品 \(i\) 放入找到的箱子中；如果找不到这样的箱子，则新开一个箱子 \(B_{k+1}\) 将 \(i\) 放入。

问题：证明 first-fit 算法的近似比为 2。
