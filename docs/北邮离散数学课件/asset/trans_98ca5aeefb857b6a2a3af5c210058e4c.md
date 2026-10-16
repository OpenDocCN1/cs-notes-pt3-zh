

# Matrix Transposition

+   如果 **A**=[*a_ij*] 是一个 *m*×*n* 矩阵，则 **A** 的 *转置*（通常写作 **A**ᵗ 或 **A**ᵀ）是 *n*×*m* 矩阵，由 **A**ᵗ = **B** = [*b_ij*] = [*a_ji*]（1≤*i*≤*n*,1≤*j*≤*m*）给出

![](img/c25dfd82fc242c2db53bc942dcad6885_2192_0.png)

# Symmetric Matrices

+   - 方阵 **A** 是 *对称矩阵* 当且仅当 **A**=**A**ᵗ。
+     *即，* ∀*i,j*≤*n*: *a_ij* = *a_ji*。
+   - 下列哪个矩阵是对称矩阵？

![](img/c25dfd82fc242c2db53bc942dcad6885_2193_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_2193_1.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_2193_2.png)

# Zero-One Matrices

+   - 用于表示其他结构。
+     - *例如，* 关系，有向图（本课程后面将介绍）
+   - *零一矩阵* 的所有元素要么是 0，要么是 1
+     - 分别表示 **False** & **True**。
+   - **A** 与 **B** 的 *join*（均为 *m×n* 零一矩阵）：
+     - **A**∨**B** := [*a*ᵢⱼ∨*b*ᵢⱼ]
+   - **A** 与 **B** 的 *meet*：
+     - **A**∧**B** := [*a*ᵢⱼ∧*b*ᵢⱼ] = [*a*ᵢⱼ *b*ᵢⱼ]

**A** 中的 1 与 **B** 中的 1 进行 join 运算，构成 **C** 中的 1。

在 **A** 中的 1 与 **B** 中的 1 进行 meet 运算的地方，我们找到了 **C** 中的 1。

# Boolean Products

+   - 设 **A**=[a_ij] 是一个 m×k 零一矩阵，且 **B**=[b_ij] 是一个 k×n 零一矩阵，
+   - **A** 与 **B** 的 *boolean product* 类似于普通矩阵乘法，但在行-列“向量点积”中使用 ∨ 代替 +：

A ⊙ B = C = [c_ij] = [∨_{ℓ=1}^k a_iℓ ∧ b_ℓj]

# EXAMPLE 8 Find the Boolean product of A and B, where

A = [1 0; 0 1; 1 0], B = [1 1 0; 0 1 1].

Solution: The Boolean product A ⊙ B is given by

A ⊙ B = [(1 ∧ 1) ∨ (0 ∧ 0) (1 ∧ 1) ∨ (0 ∧ 1) (1 ∧ 0) ∨ (0 ∧ 1); (0 ∧ 1) ∨ (1 ∧ 0) (0 ∧ 1) ∨ (1 ∧ 1) (0 ∧ 0) ∨ (1 ∧ 1); (1 ∧ 1) ∨ (0 ∧ 0) (1 ∧ 1) ∨ (0 ∧ 1) (1 ∧ 0) ∨ (0 ∧ 1)]

= [1 ∨ 0 1 ∨ 0 0 ∨ 0; 0 ∨ 0 0 ∨ 1 0 ∨ 1; 1 ∨ 0 1 ∨ 0 0 ∨ 0]

= [1 1 0; 0 1 1; 1 1 0].

# Boolean Powers

+   - 对于方阵零一矩阵 **A**，以及任何 *k*≥0，**A** 的 *kth Boolean power* 简单地是 *k* 份 **A** 的 Boolean product。

**A**^[k] := **A** ⊙ **A** ⊙ ... ⊙ **A**

**A**^[0] := *Iₙ*    *k times*

# 作业

+   - § 2.6 − 4, 20, 28, 32

# Algorithms

Rosen 7th ed., § 3.1

![](img/c25dfd82fc242c2db53bc942dcad6885_2199_0.png)

Abu al-Khwarizmi
(ca. 780-850)

# Chapter Summary

+   - Algorithms
+     - Example Algorithms
+     - Algorithmic Paradigms
+   - Growth of Functions
+     - Big-O and other Notation
+   - Complexity of Algorithms

# Section Summary

+   - Properties of Algorithms
+   - Algorithms for Searching and Sorting
+   - Greedy Algorithms
+   - Halting Problem

# Problems and Algorithms

+   - 在许多领域中，存在一些关键的一般性问题，当给定有效输入时，要求输出具有特定属性。
+   - 第一步是精确地陈述问题，使用适当的结构来指定输入和期望的输出。
+   - 然后我们通过指定一个过程的步骤来解决一般性问题，该过程接受有效输入并产生期望的输出。这个过程称为 *algorithm*。

# Algorithms

![](img/c25dfd82fc242c2db53bc942dcad6885_2204_0.png)

Abu Ja'far Mohammed Ibin Musa Al-Khowarizmi
(780-850)

**Definition**: An *algorithm* is a finite set of precise instructions for performing a computation or for solving a problem.

**Example**: Describe an algorithm for finding the maximum value in a finite sequence of integers.

**Solution**: Perform the following steps:

+   1. Set the temporary maximum equal to the first integer in the sequence.
+   2. Compare the next integer in the sequence to the temporary maximum.
+      - If it is larger than the temporary maximum, set the temporary maximum equal to this integer.
+   3. Repeat the previous step if there are more integers. If not, stop.
+   4. When the algorithm terminates, the temporary maximum is the largest integer in the sequence.

