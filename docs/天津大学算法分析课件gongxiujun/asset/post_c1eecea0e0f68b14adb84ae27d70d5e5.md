
## Definition

A decision problem is said to be in class NP (Non-deterministic Polynomial) if there exists a verifier V for the problem. Given any instance w of the problem, where the answer is "yes", there must exist a certificate (also called a witness) c such that, given the ordered pair (w,c) as input, V returns the answer "yes" in polynomial time.

- if the answer to w is "no", the verifier will return "no" with input (w,c) for all possible c.
- V could return the answer "No" even if the answer to w is "yes", if c is not a valid witness.
- Notable problems in class NP include all problems in P, graph isomorphism problem, travelling salesman problem, and boolean satisfiability problem.

## Polynomial Reduction

### Definition

If problem X can be reduced to problem Y (X ≤P Y) polynomially **if and only if** there exists a polynomial deterministic algorithm T such that

- for each input string x, T generates a string T(x)
- x is an admissible input and corresponds a “yes” answer for X **if and only if** T(x) is an admissible input and corresponds a “yes” answer for Y.

![](img/4208ee4325ab94ec0c685a689680f88f_448_0.png)

## Theorem 1

If $X \leq_P Y$ and $Y$ is in class P, then $X$ is also in class P.

### Proof

- there exists polynomial algorithm with complexity $q$ for $Y$
- let the complexity of $T$ be polynomial $p$, then the length of $T(x)$ is $O(p(|x|))$
- for input $T(x)$, complexity for $Y$ is $O(q(p(|x|)))$
- so, complexity for solving $X$ is $O(p(x) + q(p(|x|)))$

> $X \leq_P Y$ means that $Y$ is at least as hard as $X$.

## Definition

Problem Y is said to be a NP-hard problem if every problem X in class NP can be polynomially reduced to problem Y.

## Definition

Problem Y is said to be a NP-Complete (NPC) problem if Y is in class NP and Y is a NP-hard problem.

- all NPC problems consist of a closed set with respect to polynomial reduction (reflexive, symmetric, transitive).
- if there exists a polynomial algorithm for an NPC problem, then P = NP.
- we know that there are some NP-hard problems, but it is not clear whether they are in class NP (kth largest subset problem: 第 K 大子集问题).

## Kth largest subset problem

### Instance:

- A finite set A of positive integers,
- Two nonnegative integers \(K \le 2^{|A|}\) and \(B \le \sum_{a \in A} a\).

### Question: Are there at least K distinct subsets \(Y \subseteq A\) such that

\(\sum_{a \in Y} a \le B\) (1)

or

\(\left| Y \subseteq A : \sum_{a \in Y} a \le B \right| \ge K\) (2)

## Euler Diagram

![](img/4208ee4325ab94ec0c685a689680f88f_452_0.png)

## Lists of NP-Complete Problems

- Boolean satisfiability problem (SAT)
- N-puzzle
- Knapsack problem
- Hamiltonian path problem
- Traveling salesman problem
- Subgraph isomorphism problem
- Subset sum problem
- Clique problem
- Vertex cover problem
- Independent set problem
- Graph coloring problem

## Summary

### N- Nondeterministic Algorithms

- Deterministic algorithm: Given a particular input, it will always produce the same correct output
- Non-deterministic algorithm: with one or more choice points where multiple different continuations are possible, without any specification of which one will be taken

### P- Polynomial Time Complexity

- Computable
- Polynomial time is assumed to be the lowest complexity

### C- Complete Transformation Closed

- Reducible

Coming up: The End.

Thank You
