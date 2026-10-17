

## Calculating expectation

E[T(n)] = E[Σ_{k=0}^{n-1} X_k(T(k) + T(n-k-1) + Θ(n))]

= Σ_{k=0}^{n-1} E[X_k(T(k) + T(n-k-1) + Θ(n))]

= Σ_{k=0}^{n-1} E[X_k] · E[T(k) + T(n-k-1) + Θ(n)]

Independence of X_k from other random choices.

= (1/n) Σ_{k=0}^{n-1} E[T(k)] + (1/n) Σ_{k=0}^{n-1} E[T(n-k-1)] + (1/n) Σ_{k=0}^{n-1} Θ(n)

Linearity of expectation; E[X_k] = 1/n .

= (2/n) Σ_{k=1}^{n-1} E[T(k)] + Θ(n)

Summations have identical terms.

## Hairy recurrence

E[T(n)] = (2/n) Σ_{k=2}^{n-1} E[T(k)] + Θ(n)

(The k=0, 1 terms can be absorbed in the Θ(n).)

**Prove:** E[T(n)] ≤ an lg n for constant a > 0.

- Choose a large enough so that an lg n dominates E[T(n)] for sufficiently small n ≥ 2.

**Use fact:** Σ_{k=2}^{n-1} k lg k ≤ (1/2)n² lg n - (1/8)n² (exercise).

## Substitution method

E[T(n)] ≤ (2/n) Σ_{k=2}^{n-1} ak lg k + Θ(n)

Substitute inductive hypothesis.

≤ (2a/n)(1/2 n² lg n - 1/8 n²) + Θ(n)

Use fact.

= an lg n - (an/4 - Θ(n))

≤ an lg n ,

if a is chosen large enough so that an/4 dominates the Θ(n).

![](img/5e59105b951890406cf98b2a964cb2f9_328_0.png)

## Quicksort in practice

- Quicksort is a great general-purpose sorting algorithm.
- Quicksort is typically over twice as fast as merge sort.
- Quicksort can benefit substantially from *code tuning*.
- Quicksort behaves well even with caching and virtual memory.

# Introduction to Algorithms

6.046J/18.401J

![](img/5e59105b951890406cf98b2a964cb2f9_329_0.png)

# LECTURE 5

- Sorting Lower Bounds
- Decision trees
- Linear-Time Sorting
- Counting sort
- Radix sort
- Appendix: Punched cards

Prof. Erik Demaine

## How fast can we sort?

All the sorting algorithms we have seen so far are **comparison sorts**: only use comparisons to determine the relative order of elements.

- E.g., insertion sort, merge sort, quicksort, heapsort.

The best worst-case running time that we’ve seen for comparison sorting is _O_(_nlg n_).

## Is _O_(_nlg n_) the best we can do?

**Decision trees** can help us answer this question.

## Decision-tree example

Sort <a₁, a₂, ..., aₙ>

![](img/5e59105b951890406cf98b2a964cb2f9_331_0.png)

Each internal node is labeled i:j for i, j ∈ {1, 2,..., n}.

- The left subtree shows subsequent comparisons if a_i ≤ a_j.
- The right subtree shows subsequent comparisons if a_i ≥ a_j.

## Decision-tree example

Sort \(\langle a_1, a_2, a_3 \rangle\)
\(= \langle 9, 4, 6 \rangle\):

![](img/5e59105b951890406cf98b2a964cb2f9_333_0.png)

Each internal node is labeled \(i:j\) for \(i, j \in \{1, 2, \dots, n\}\).

- The left subtree shows subsequent comparisons if \(a_i \leq a_j\).
- The right subtree shows subsequent comparisons if \(a_i \geq a_j\).

## Decision-tree example

Sort <a1, a2, a3> = <9, 4, 6>:

![](img/5e59105b951890406cf98b2a964cb2f9_335_0.png)

4 ≤ 6 ≤ 9

Each leaf contains a permutation ⟨π(1), π(2),..., π(n)⟩ to indicate that the ordering a_π(1) ≤ a_π(2) ≤ ⋯ ≤ a_π(n) has been established.

