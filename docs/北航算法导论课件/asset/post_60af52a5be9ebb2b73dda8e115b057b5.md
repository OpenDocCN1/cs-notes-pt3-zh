
## 5.3.2 Randomly permuting an array
## (2) RANDOMIZE-IN-PLACE

```
RANDOMIZE-IN-PLACE(A, n)
for (i=1; i<=n; i++)
    swap(A[i], A[RANDOM(i, n)])
```

Lemma  RANDOMIZE-IN-PLACE computes a uniform random permutation.

Proof  Loop invariant: Pr{A[1..i-1] contains each (i-1)-permutation} = (n-i+1)!/n!.

- **Maintenance:**

… …

Pr{E₂ ∩ E₁} = Pr{E₂|E₁} Pr{E₁}.

The algorithm choose xᵢ randomly from the n-i+1 possibilities in A[i..n] => Pr{E₂|E₁} = 1/(n-i+1)? Thus,

| i | i+1 | … | n |
|---|---|---|---|
| A(jᵢ) | A(jᵢ₊₁) | … | A(jₙ) |

Pr{E₂ ∩ E₁} = Pr{E₂|E₁} Pr{E₁}
= 1/(n-i+1) · (n-i+1)!/n! = (n-i)!/n!

**Proof**  **Loop invariant:** Pr{A[1 . . i−1] contains each (i−1)-permutation} = (n−i+1)!/n!.

- **Termination:**

At termination, i=n+1, it is true prior to the ith iteration, so we conclude that A[i . . n] is a given n-permutation with probability (n−n)!/n! = 1/n!.

■ (lemma)

## *5.4 Further applications

- 自学

## Exercises and problems

- **Exercises**
  - 所有课后习题。
  - 编程验证习题。
- **Class-exercises**
  - 雇用问题中，仅雇用1个人的概率，即 Pr(X=1)？
  - 雇用问题中，n个人都会被雇佣的概率，即 Pr(X=n)？
  - 雇用问题中，仅雇用2个人的概率，即 Pr(X=2)？

## Part IV:
## Advanced Design and Analysis Techniques

高级、先進的设计与分析方法、技术

## Advanced Design and Analysis Techniques
## □ Dynamic programming

- Not a specific algorithm, but a technique (like divide-and-conquer).
- “programming” means “tabular method”, not computer programming. （programming表示列表方法，而不是指编程）
- Used for optimization problems (assembly-line scheduling).

## □ Greedy algorithms

- To make each choice in a locally optimal manner. (coin-changing)
  （以局部最优方式作每一次选择）

- ……

- Enumeration（穷举法）

- Divide-and-conquer: the solution of recurrences

- Backtrack（回溯）

- Randomization

## 15 Dynamic Programming

- **Scheduling two automobile assembly lines** （流水线、装配线调度）
- **Matrix-chain multiplication** （矩阵链相乘，矩阵连乘）
- **Characteristics of dynamic programming**
  （动态规划法的特征）
- **Longest common subsequence** （最长相同子序列）
- **Optimal binary search trees** （最优二叉搜索树）
- **Steel rod cutting** （钢条、钢管切割）

## 15.1 Assembly-line scheduling

Automobile factory with two assembly lines: A manufacturing problem to find the fastest way through a factory. （汽车制造有两条流水线，求汽车制造的流水线调度的最快方法）

![](img/09c68ab421cfce4995ddad1430ef2637_231_0.png)

Problem: determine which stations to choose from line 1 and which to choose from line 2 in order to minimize the total time through the factory for one auto. （应选line1中哪一个装配站, line2中哪一个装配站, s.t. 装配一个汽车的开销最小）

## 15.1 Assembly-line scheduling

- The fastest way through the factory

![](img/09c68ab421cfce4995ddad1430ef2637_232_0.png)

f* = 2+7+2+5+1+3
+1+4+5+1+4+3=38

![](img/09c68ab421cfce4995ddad1430ef2637_232_1.png)

- How to find the fastest way?

## 15.1 Assembly-line scheduling

![](img/09c68ab421cfce4995ddad1430ef2637_233_0.png)

- “brute force” way (enumerate all the way) infeasible when there are many stations.
  （原始方法，穷举法，当stations n 很大时，穷举法实际不可行）
- If it is given a list of which stations to use in line 1 and which to use in line 2, it is easy to compute in Θ(n) time how long it takes a chassis to pass through the factory.
  （当给定line1和line2中哪些station被使用，需要Θ(n)时间去计算该装配过程）
- There are 2ⁿ possible ways to choose stations. By enumerating all possible ways and computing how long each takes would require Ω(2ⁿ) time, infeasible when n is large.
  （从line1和line2中选择不同的station，共有 2ⁿ 种方法通过工厂，列举每个过程，并计算每个过程的开销，共需要Ω(2ⁿ)）

## Step 1: The structure of the fastest way through the factory

![](img/09c68ab421cfce4995ddad1430ef2637_234_0.png)

- **Characterize the structure of an optimal solution.**
  （特征化一个最优解的结构）

- **Consider the fastest possible way for a chassis to get from the starting point through station S₁ⱼ.**
  （考虑这种情况：一个底盘从装配线的入口点开始，以最快的方式通过 station S₁ⱼ。问：这条路径是什么？）

- **If j = 1, there is only one way that the chassis could have gone. It is easy to determine how long it takes to get through station S₁ⱼ.**
  （若 j = 1，则只有一种方式通过 S₁,₁）
