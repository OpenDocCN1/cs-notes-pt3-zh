

## VLSI layout

**Problem:** Embed a complete binary tree with \( n \) leaves in a grid using minimal area.

![](img/5e59105b951890406cf98b2a964cb2f9_274_0.png)

\( H(n) = H(n/2) + \Theta(1) \)
\( = \Theta(\lg n) \)

\( H(n) = H(n/2) + \Theta(1) = \Theta(\lg n) \)

\( W(n) = 2 W(n/2) + \Theta(1) = \Theta(n) \)

$H(n) = H(n/2) + \Theta(1)$  
$= \Theta(\lg n)$

$W(n) = 2W(n/2) + \Theta(1)$  
$= \Theta(n)$

**Area** $= \Theta(n \lg n)$

## H-tree embedding

![](img/5e59105b951890406cf98b2a964cb2f9_278_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_279_0.png)

L(n) = 2 L(n/4) + Θ(1)
= Θ(√n)

Area = Θ(n)

![](img/5e59105b951890406cf98b2a964cb2f9_280_0.png)

## Conclusion

- Divide and conquer is just one of several powerful techniques for algorithm design.
- Divide-and-conquer algorithms can be analyzed using recurrences and the master method (so practice this math).
- The divide-and-conquer strategy often leads to efficient algorithms.

# Introduction to Algorithms

6.046J/18.401J

![](img/5e59105b951890406cf98b2a964cb2f9_282_0.png)

# LECTURE 4

- Quicksort
- Divide and conquer
- Partitioning
- Worst-case analysis
- Intuition
- Randomized quicksort
- Analysis

## Quicksort

- Proposed by C.A.R. Hoare in 1962.
- Divide-and-conquer algorithm.
- Sorts “in place” (like insertion sort, but not like merge sort).
- Very practical (with tuning).

## Divide and conquer

Quicksort an \(n\)-element array:

1. **Divide**: Partition the array into two subarrays around a **pivot** \(x\) such that elements in lower subarray \(\le x \le\) elements in upper subarray.

![](img/5e59105b951890406cf98b2a964cb2f9_284_0.png)

2. **Conquer**: Recursively sort the two subarrays.

3. **Combine**: Trivial.

**Key**: Linear-time partitioning subroutine.

## Partitioning subroutine

PARTITION(A, p, q) ▷ A[p .. q]
x ← A[p] ▷ pivot = A[p]
i ← p
for j ← p + 1 to q
do if A[j] ≤ x
then i ← i + 1
exchange A[i] ↔ A[j]
exchange A[p] ↔ A[i]
return i

> Running time
> = O(n) for n
> elements.

## Invariant:

![](img/5e59105b951890406cf98b2a964cb2f9_285_0.png)

## Example of partitioning

![](img/5e59105b951890406cf98b2a964cb2f9_286_0.png)

i j

| 6 | 10 | 13 | 5 | 8 | 3 | 2 | 11 |
|---|---|---|---|---|---|---|---|

![](img/5e59105b951890406cf98b2a964cb2f9_287_0.png)

## Example of partitioning

![](img/5e59105b951890406cf98b2a964cb2f9_288_0.png)

## Example of partitioning

![](img/5e59105b951890406cf98b2a964cb2f9_289_0.png)

## Example of partitioning

| 6 | 10 | 13 | 5 | 8 | 3 | 2 | 11 |
|---|---|---|---|---|---|---|---|
| 6 | 5 | 13 | 10 | 8 | 3 | 2 | 11 |

i → j

## Example of partitioning

| 6 | 10 | 13 | 5 | 8 | 3 | 2 | 11 |
|---|---|---|---|---|---|---|---|
| 6 | 5 | 13 | 10 | 8 | 3 | 2 | 11 |

i j

## Example of partitioning

![](img/5e59105b951890406cf98b2a964cb2f9_292_0.png)

## Example of partitioning

![](img/5e59105b951890406cf98b2a964cb2f9_294_0.png)

## Example of partitioning

![](img/5e59105b951890406cf98b2a964cb2f9_296_0.png)

## Example of partitioning

![](img/5e59105b951890406cf98b2a964cb2f9_297_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_297_1.png)

$i$

