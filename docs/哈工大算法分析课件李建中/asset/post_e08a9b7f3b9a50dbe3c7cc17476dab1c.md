
## 5.6 The Optimal Binary Search Trees

## 问题的定义

- 二叉搜索树 T
  - 特征：
    - K={k1,k2,...,kn}
    - D={d0,d1,...,dn}
    - d_i 处于 k_i 与 k_{i+1} 之间, d0 处于 k1 左侧, dn 处于 kn 右侧
  - 附加信息：
    - 设关键字 k_i 搜索概率为 p_i
    - 设 d_i 搜索概率为 q_i
    - Σ_{i=1}^n p_i + Σ_{i=0}^n q_i = 1

## 搜索树的期望代价

E(T)= Σ_{i=1}^n (DEP_T(k_i)+1)p_i + Σ_{i=0}^n (DEP_T(d_i)+1)q_i

## 问题的定义

输入：K={k1,k2,...,kn}, k1<k2<...<kn
P={p1,p2,...,pn}, p_i 为搜索关键字 k_i 的概率
Q={q0,q1,...,qn}, q_i 为搜索值 d_i 的概率
输出：构造最优二叉搜索树 T，使得
E(T)= Σ_{i=1}^n (DEP_T(k_i)+1)p_i + Σ_{i=0}^n (DEP_T(d_i)+1)q_i
最小

## 优化二叉搜索树的构造与分析

- 树构造问题
  K={k1,k2,...,kn} 的最优搜索树包含每个 k_i

## 优化子结构

定理：若最优二叉搜索树 T 包含关键字集合 {k_r,k_{r+1},...,k_s} 则 T 的左子树是关键字集合 {k_r,k_{r+1},...,k_{s-1}} 的最优搜索树，右子树是关键字集合 {k_{r+1},...,k_s} 的最优搜索树。

## 用优化子结构构造优化解

K=(k_p,k_{p+1},...,k_j)为优化解则其前k_p个k_i

![](img/9e822ee25d7fb44c33253ed3ff372fc1_55_0.png)

若k_p≠k_{p+1}，则k_p,k_{p+1},...,k_j 与 k_{p+1},...,k_j 为优化解，则可由优化解构造优化解

若k_p=k_{p+1}，则k_p,k_{p+1},...,k_j 与k_p,k_{p+1},...,k_j 为优化解，d_{i,j}=q_{i,j}，若k_p≠k_{p+1}则d_{i,j}=q_{i,j}

## 递推优化解的递推方程

令E(i,j)为k_p,...,k_j为优化解T_{i,j}的期望费用递推

- 当j=i-1，T_{i,j}为空树则E(i,i-1)=q_{i,i}
- 当j≥i，则存在一个k_p∈{k_p,...,k_j}

![](img/9e822ee25d7fb44c33253ed3ff372fc1_55_1.png)

当i≤j时优化子结构T_{i,j}，每个子树的期望费用≥0

E(i,j)=P_{i,j}+E(i,k-1)+W(i,r+1)+E(r+1,j)+W(i,r+1,j)

## 计算W(i,r-1)与W(r+1,j)

E(LT+1)=∑_{k=1}^{i}(DEP_{k}(k_i)+2)p_i + ∑_{k=1}^{j}(DEP_{k}(d_j)+2)q_j

E(LT)=∑_{k=1}^{i}(DEP_{k}(k_i)+1)p_i + ∑_{k=1}^{j}(DEP_{k}(d_j)+1)q_j

则 W(i,r-1)=E(LT+1)-E(LT)=∑_{i=1}^{r} p_i ∑_{j=i+1}^{r} q_j

同理，W(r+1,j)=∑_{i=r+1}^{j} p_i ∑_{j=i+1}^{j} q_j

W(i,j)=W(i,r-1)+W(r+1,j)+p_r q_r ≥ ∑_{i=1}^{r} p_i ∑_{j=i+1}^{j} q_j =W(i,j-1)+p_j+q_j

W(i,i-1)=q_{i,i}

W(i,j)=W(i,r-1)+W(r+1,j)+p_r=W(i,i-1)p_j+q_j

E(i,j)=P_{i,j}+E(i,k-1)+W(i,r+1)+E(r+1,j)+W(r+1,j)

![](img/9e822ee25d7fb44c33253ed3ff372fc1_55_2.png)

E(i,j)=E(i,r-1)+E(r+1,j)+W(i,j)

![](img/9e822ee25d7fb44c33253ed3ff372fc1_55_3.png)

结论

E(i,j)=q_{i,i}  if j=i-1
E(i,j)=min_{r≤i}[E(i,r-1)+E(r+1,j)+W(i,j)]  if j≥i
W(i,i-1)=q_{i,i}  W(i,j)=W(i,j-1)+p_j+q_j

## 自下而上计算优化解的递推表

E(i,j)=q_{i,i}  if j=i-1
E(i,j)=min_{r≤i}[E(i,r-1)+E(r+1,j)+W(i,j)]  if j≥i

q0: E(1,0) E(1,1) E(1,2) E(1,3) E(1,4)
q1: E(2,1) E(2,2) E(2,3) E(2,4)
q2: E(3,2) E(3,3) E(3,4)
q3: E(4,3) E(4,4)
q4: E(5,4)

![](img/9e822ee25d7fb44c33253ed3ff372fc1_56_0.png)

![](img/9e822ee25d7fb44c33253ed3ff372fc1_56_1.png)

![](img/9e822ee25d7fb44c33253ed3ff372fc1_56_2.png)

![](img/9e822ee25d7fb44c33253ed3ff372fc1_56_3.png)

## Homework 2: 优化解的构造算法

## Greedy Algorithm

- 6.1 Elements of Greedy Algorithms
- 6.2 An activity-selection problem
- 6.3 Huffman codes
- 6.4 Minimal spanning tree problem
- 6.5 Theoretical foundations of Greedy Algorithms
- 6.6 A task-scheduling problem

## Chapter 5

Pages 138-184

## 6.1 Elements of Greedy Algorithms

- Greedy算法的基本概念
- Greedy算法是局部最优的选择
- Greedy算法的设计方法

## Greedy算法的基本概念

- Greedy算法的实例
  - 最短路径问题
- Greedy算法过程

![](img/9e822ee25d7fb44c33253ed3ff372fc1_57_0.png)

Greedy算法不是完美的全局最优解

## Greedy算法的基本思想

- 每一步都做出局部最优的选择，以期得到全局最优解
- 一步一步地构造解
- 决策点有当前最优的选择
- 需要证明该选择能够导致最终达到全局最优解
- Greedy算法不一定能产生全局最优解
- Greedy算法要满足的两个基本性质
  - Greedy-choice-property
  - Optimal substructure

## Greedy性质

- 每个优化问题都具有优化解的一个过程是解此问题的一种解法，如果问题具有 Greedy 性质
- 一个问题是否具有 Greedy 性质需要证明

## 优化子结构

若一个优化问题的优化解包含子问题的优化解，则该问题具有优化子结构

## 动态规划方法或 Greedy 方法

- 动态规划方法可用条件
  - 优化子结构
  - 具有重叠子问题
- Greedy 方法可用条件
  - 优化子结构
  - Greedy 性质
- 可用 Greedy 方法时，动态规划方法可能不适用
- 可用动态规划方法时，Greedy 方法可能不适用

## 描述 Greedy 算法的设计方法

1. 设计含心设计方法：
   - 含心设计方法
   - 制定贪心准则
2. 证明：对1中含心设计方法，所含心问题具有优化子结构
   证明：对1中含心设计方法所含心问题具有 Greedy 性质
3. 依据1中设计含心设计方法计算方法

## 6.2 An activity-selection problem

- 问题定义
- 设计含心选择方法
- 优化解的性质分析
- Greedy 性质
- 算法设计
- 算法复杂性分析

## 问题的定义

活动
设 S={1,2,...,n} 是 n 个活动集合，所有活动共享同一资源，使其最多可同时进行一个活动使用
每个活动 i 有开始时间 s_i，结束时间 f_i，s_i ≤ f_i
相容活动
两个活动 i 和 j 相容，若 s_j ≥ f_i 或 s_i ≥ f_j

![](img/9e822ee25d7fb44c33253ed3ff372fc1_58_0.png)
