

## Bounding solution states

We have known that **greedy algorithm** can find the optimal value for fractional knapsack problem.

**Fractional relaxation:** The optimal value for fractional knapsack problem is the **upper bound** of 0/1 knapsack problem

Therefore,

- we can calculate **upper bound** for each sub problem (corresponding to a solution state)
- also, its **lower bound** corresponds to the value of current packing
- the **upper/lower bound** can guide the search for the optimal solution;
- for each state, its lower bound should no larger than upper bound
- for two states A and B, if A’s upper bound is no larger than B’s lower bound, then A should be discarded

## State space tree with lower/upper bounds

(n=4,c=7,p=[4,7,9,10], w=[1,2,3,5])

![](img/4208ee4325ab94ec0c685a689680f88f_334_0.png)

- for node 1, upper bound=4+7+9+(7-1-2-3)*(10/5)=22, lower bound=0
- for node 2, upper bound=4+7+9+(7-1-2-3)*(10/5)=22, lower bound=4

## Problem statements

- **Branch & Bound** (BB) is an enhancement of backtracking for searching solution space with bounding, respect to a global optimization problem (min/max, for simplicity, just consider the min problem)

$$\min_{x \in S} f(x)$$  (1)

where $x=(x_1,x_2,\cdots,x_n)$, $x\in S_i$, $S=S_1\cup S_2\cup\cdots\cup S_n$, and each $S_i$ is a limited set. Usually, $x$ is constrained with

$$g(x)<b$$  (2)

- It consists of systematic enumeration of all candidate solutions, discarding large subsets of fruitless candidates by using **upper** and **lower** estimated bounds of quantity being optimized

- The implementation of this approach is a modification of the **breadth-first** search with branch-and-bound pruning.

