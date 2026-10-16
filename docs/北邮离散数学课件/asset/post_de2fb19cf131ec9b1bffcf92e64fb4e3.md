
# Matrix Transposition

+   If **A**=[*a_ij*] is an *m*×*n* matrix, the *transpose* of **A** (often written **A**ᵗ or **A**ᵀ) is the *n*×*m* matrix given by **A**ᵗ = **B** = [*b_ij*] = [*a_ji*] (1≤*i*≤*n*,1≤*j*≤*m*)

![](img/c25dfd82fc242c2db53bc942dcad6885_2192_0.png)

# Symmetric Matrices

+   - A square matrix **A** is *symmetric* iff **A**=**A**ᵗ.
+     *I.e.,* ∀*i,j*≤*n*: *a_ij* = *a_ji*.
+   - Which of the below matrices is symmetric?

![](img/c25dfd82fc242c2db53bc942dcad6885_2193_0.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_2193_1.png)

![](img/c25dfd82fc242c2db53bc942dcad6885_2193_2.png)

# Zero-One Matrices

+   - Useful for representing other structures.
+     - *E.g.,* relations, directed graphs (later in this course)
+   - All elements of a *zero-one* matrix are either 0 or 1
+     - Representing **False** & **True** respectively.
+   - The *join* of **A**, **B** (both *m×n* zero-one matrices):
+     - **A**∨**B** := [*a*ᵢⱼ∨*b*ᵢⱼ]
+   - The *meet* of **A**, **B**:
+     - **A**∧**B** := [*a*ᵢⱼ∧*b*ᵢⱼ] = [*a*ᵢⱼ *b*ᵢⱼ]

The 1’s in **A** join the 1’s in **B** to make up the 1’s in **C**.

Where the 1’s in **A** meet the 1’s in **B**, we find 1’s in **C**.

# Boolean Products

+   - Let **A**=[a_ij] be an m×k zero-one matrix, & let **B**=[b_ij] be a k×n zero-one matrix,
+   - The *boolean product* of **A** and **B** is like normal matrix ×, but using ∨ instead of + in the row-column “vector dot product”:

A ⊙ B = C = [c_ij] = [∨_{ℓ=1}^k a_iℓ ∧ b_ℓj]

# EXAMPLE 8 Find the Boolean product of A and B, where

A = [1 0; 0 1; 1 0], B = [1 1 0; 0 1 1].

Solution: The Boolean product A ⊙ B is given by

A ⊙ B = [(1 ∧ 1) ∨ (0 ∧ 0) (1 ∧ 1) ∨ (0 ∧ 1) (1 ∧ 0) ∨ (0 ∧ 1); (0 ∧ 1) ∨ (1 ∧ 0) (0 ∧ 1) ∨ (1 ∧ 1) (0 ∧ 0) ∨ (1 ∧ 1); (1 ∧ 1) ∨ (0 ∧ 0) (1 ∧ 1) ∨ (0 ∧ 1) (1 ∧ 0) ∨ (0 ∧ 1)]

= [1 ∨ 0 1 ∨ 0 0 ∨ 0; 0 ∨ 0 0 ∨ 1 0 ∨ 1; 1 ∨ 0 1 ∨ 0 0 ∨ 0]

= [1 1 0; 0 1 1; 1 1 0].

# Boolean Powers

+   - For a square zero-one matrix **A**, and any *k*≥0, the *kth Boolean power of* **A** is simply the Boolean product of *k* copies of **A**.

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

+   - In many domains there are key general problems that ask for output with specific properties when given valid input.
+   - The first step is to precisely state the problem, using the appropriate structures to specify the input and the desired output.
+   - We then solve the general problem by specifying the steps of a procedure that takes a valid input and produces the desired output. This procedure is called an *algorithm*.

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
