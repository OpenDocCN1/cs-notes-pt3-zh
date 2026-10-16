
## Step 1: The structure of the fastest way through the factory

- To characterize the structure of an optimal solution.
- Considering the fastest possible way for a chassis to get from the starting point through station $S_{1,j}$. （从装配线的入口点开始，以最快的方式通过 $S_{1,j}$，这条路径是什么？）
- If $j=1$, only one way

![](img/09c68ab421cfce4995ddad1430ef2637_235_0.png)

- **For $j \ge 2$, two choices**
  - through $S_{1,j-1}$, then **directly** to $S_{1,j}$, no transfer time;
  - through $S_{2,j-1}$, then **transfer over** to station $S_{1,j}$, transfer time $t_{2,j-1}$.
  - These two possibilities have much in common.

## Step 1: The structure of the fastest way through the factory

- **First, suppose that the fastest way through station $S_{1j}$ is through station $S_{1,j-1}$.**

（首先，设以最快方式通过 $S_{1j}$ 的路径为 $p_j$，$p_j$ 中的 $S_{1j}$ 的前一个 station 是 $S_{1,j-1}$）

![](img/09c68ab421cfce4995ddad1430ef2637_236_0.png)

- **The chassis must have taken a fastest way from the starting point through station $S_{1,j-1}$. Why?** （去掉路径 $p_j$ 中的最后一个 $S_{1j}$ 后得到 $p_{j-1}$，则 $p_{j-1}$ 是通过 $S_{1,j-1}$ 的最快路径）

- If there were **another faster way** to get through station $S_{1,j-1}$, we could **substitute** this faster way to yield **another faster way** through station $S_{1j}$: a **contradiction**.

（若有另外一条更快的路径 $q_{j-1}$ 通过 $S_{1,j-1}$，则用 $q_{j-1}$ 替换 $p_{j-1}$，那么 $q_j=q_{j-1}+S_{1,j}$ 是比 $p_j$ 更快的路径，矛盾）

## Step 1: The structure of the fastest way through the factory

![](img/09c68ab421cfce4995ddad1430ef2637_237_0.png)

- **Similarly,** suppose that the fastest way through station $S_{1j}$ is through station $S_{2j-1}$.

- The chassis must have taken a fastest way from the starting point through station $S_{2j-1}$. The reasoning is the same:
  - If there were another faster way to get through station $S_{2j-1}$, we could substitute this faster way to yield another faster way through station $S_{1j}$: a contradiction.

## Step 1: The structure of the fastest way through the factory

- **Optimal substructure**
  （最佳子结构）
  - An optimal solution to a problem (assembly-line scheduling, finding the fastest way through station $S_{i,j}$) **contains within it** an optimal solution to subproblems (finding the fastest way through either $S_{1,j-1}$ or $S_{2,j-1}$).
  （问题的最优解包含其子问题的最优解，$p_j$ contains $p_{j-1}$ within it.）
  - We refer to this property as *optimal substructure*.
  - Optimal substructure is one of the hallmarks of the applicability of dynamic programming.
  （为什么使用动态规划法？最佳子结构是其特点之一）

![](img/09c68ab421cfce4995ddad1430ef2637_238_0.png)

## Step 1: The structure of the fastest way through the factory

- Use optimal substructure to construct an optimal solution to a problem from optimal solutions to subproblems.

（使用最佳子结构可以从子问题的最优解来构造原问题的最优解）

![](img/09c68ab421cfce4995ddad1430ef2637_239_0.png)

- First, fastest way through $S_{1,j}$ is either:
  - fastest way through $S_{1,j-1}$ then directly through $S_{1,j}$, or
  - fastest way through $S_{2,j-1}$, transfer from line 2 to line 1, then through station $S_{1,j}$.

（通过 $S_{1,j}$ 的最快方法有两种，一种是先通过 $S_{1,j-1}$，然后直接通过 $S_{1,j}$，另一种先通过 $S_{2,j-1}$，然后从line2转移到line1，再通过 $S_{1,j}$）

- Symmetrically reasoning, through station $S_{2,j}$.

## Step 2: A recursive solution

- Define the value of an optimal solution recursively in terms of the optimal solutions to subproblems.
  （通过子问题的最优解来递归地定义原问题的最优解）
- Subproblems: finding the fastest way through station j on both lines, for j = 1, 2, ..., n.
  （子问题：寻找通过任意station j (= 1, 2, ..., n)的最快路径）
- Let f[i,j] = fastest time to through S_{i,j} from the starting point.
  （从入口点开始，设以最快方式通过station S_{i,j}的时间为f[i,j]）

![](img/09c68ab421cfce4995ddad1430ef2637_241_0.png)

## Step 2: A recursive solution

- **Let** $f[i,j]$ **= fastest time to through** $S_{i,j}$ **from the starting point.**

（从入口点开始，设以最快方式通过 station $S_{i,j}$ 的时间为 $f[i,j]$）

![](img/09c68ab421cfce4995ddad1430ef2637_242_0.png)

- **Ultimate goal: fastest time to get a chassis all the way through the factory** $= f^*$.

  The chassis has to get all the way through station $n$ on either line 1 or line 2, and then to the factory exit.

（目标：以最快方式通过整个装配过程，设该时间为 $f^*$。最后一步是在 line 1 or line 2 上通过 station $n$，然后直接退出装配线）

$f^* = \min(f_1[n] + x_1, f_2[n] + x_2) \qquad (15.1)$
