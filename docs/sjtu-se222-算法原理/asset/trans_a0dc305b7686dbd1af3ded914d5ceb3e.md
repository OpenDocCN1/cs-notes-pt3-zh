

## 排序问题

Problem: Sorting
Input: An array A[1..n] of n elements
Output: The sorted array of A[1..n]

![](img/a8f1b433a70f1e5c410c8b43e41b650e_922_0.png)

n! leaves

□log(n!)□ = Θ(nlogn)

## 决策树

Definition: Simple Decision tree model

Every decision is based on the comparison of two numbers within constant time

Definition: Algebra Decision tree model

Every decision is based on some polynomial function:

f(x₁,x₂,...,xₙ) = 0?

## 元素唯一性

**Problem:** ElementUniqueness  
**Input:** A set of *n* numbers  
**Output:** *yes*, if there does not exist two of them that are equal; *no*, otherwise

> **Theorem**  
> Any algorithm base on *algebraic decision tree model* to determine element uniqueness requires **Ω(nlogn)** comparisons in the worst case.

## 路线图

- Decision tree model
- Linear-time reduction

## 多项式时间归约

*Q is polynomially reduced to Q′*

![](img/a8f1b433a70f1e5c410c8b43e41b650e_926_0.png)

Polynomial-time

Q ⪯ₚ Q′: Q′ is harder than Q

> Review (P v.s. NP)

## 线性时间归约

A ⪯ₗ B: A has lower bound Ω(f(n)) implies B has lower bound Ω(f(n))

f(n) = Ω(n)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_927_0.png)

## 凸包问题

![](img/a8f1b433a70f1e5c410c8b43e41b650e_928_0.png)

Sorting 𝒪(nlog n) ConvexHull

## 最近点对问题

![](img/a8f1b433a70f1e5c410c8b43e41b650e_929_0.png)

ElementUniqueness ≤ₗ ClosestPair

## 欧几里得最小生成树问题

![](img/a8f1b433a70f1e5c410c8b43e41b650e_930_0.png)

## Lecture 14 Approximation algorithms

- Approximation algorithms
- Hardness result: Traveling sales man problem
- Easiness result: Subset Sum problem

## 近似算法

An approximation algorithm for an optimization problem Π is a (polynomial time) algorithm such that given an instance I, it outputs some solution.

Approximation ratio

|A(I) - OPT(I)|

or

A(I) / OPT(I)

Reason1.

Planar graph coloring problem

|A(I) - OPT(I)| < 4

Reason2.

Knapsack problem

for any k. there DOES NOT exist A, s.t.
|A(I) - OPT(I)| <= k

## 我们在哪里？

- Approximation algorithms:
  - Vertex cover problem
  - Knapsack problem
  - Euclidean TSP problem
- Hardness result: Traveling Sales Person problem
- Easiness result: Subset Sum problem

## 顶点覆盖问题

![](img/a8f1b433a70f1e5c410c8b43e41b650e_936_0.png)

None is correct.
Which one has the best approx. ratio?

Algorithm1: Pick up a node v --> delete v and all edges incident to v.
R1 = ∞

Algorithm2: Pick up an edge e(u,v) --> add u, v to the cover --> delete all edges incident to u,v.
R2 <= 2

Algorithm3(Greedy): Pick up a node v with max degree --> delete v and all edges incident to v.
R3 = ∞

## VC - Greedy

![](img/a8f1b433a70f1e5c410c8b43e41b650e_937_0.png)

R >= ln n

## 贪心求解背包问题

Algorithm1: Repeatedly choose the item with the largest value/size ratio.

What about U={u1,u2}, v1=2, s1=1; v2=s2=C>2?

R1 = ∞

Algorithm2: Repeatedly choose the item with the largest value/size ratio. Then compare the total value with the item with maximum value.

R2 <= 2

## 贪心求解背包问题

```
**Algorithm 15.3 KNAPSACKGREEDY**

**Input:** `2n + 1` positive integers corresponding to item sizes `(s₁, s₂, …, sₙ)`, item values `(v₁, v₂, …, vₙ)` and the knapsack capacity `C`.

**Output:** A subset `Z` of the items whose total size is at most `C`.

1. Renumber the items so that `v₁/s₁ ≥ v₂/s₂ ≥ ⋯ ≥ vₙ/sₙ`.
2. `j ← 0; K ← 0; V ← 0; J ← ∅`
3. **while** `j < n` and `K < C`
4. `j ← j + 1`
5. **if** `sⱼ ≤ C − K` **then**
6. `Z ← Z ∪ {j}; K ← K + sⱼ; V ← V + vⱼ`
7. **end if**
8. **end while**
```

![](img/a8f1b433a70f1e5c410c8b43e41b650e_939_0.png)

## R <= 2

Let X = {u1, u2, ..., um} be the set of items of an optimal solution, assuming

v_j / s_j ≥ v_{j+1} / s_{j+1}.

If |X| ≤ 1 then the solution of the algorithm is optimal. So suppose |X| > 1. Let u_m be the first item of X not included into the knapsack by the algorithm. If no such items exists then the output of the algorithm is optimal. So assume that u_m exists.

The optimal solution can be rewritten as

OPT(I) = Σ_{j=1}^{m-1} v_j + Σ_{j=m}^{z} v_j

Let W denote the set of items packed by the algorithm before u_m but not in {u1, u2, ..., u_{m-1}}. In other words, u_j ∈ W iff u_j ∉ {u1, u2, ..., u_{m-1}} and

v_j / s_j ≥ v_m / s_m

Now A(I) can be written as

A(I) ≥ Σ_{j=1}^{m-1} v_j + Σ_{j∈W} v_j

Let

C' = C - Σ_{j=1}^{m-1} s_j

and

C'' = C' - Σ_{u_j ∈ W} s_j

By the definition of u_m, we have

C'' < s_m

