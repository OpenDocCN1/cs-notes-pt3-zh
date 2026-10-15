
## Selection Sort Running Times

- Many algorithms that operate on vectors have running times that are proportional to the size of the array. If you multiply the number of values by ten, you would expect those algorithms to take ten times as long.
- As the running times on the preceding slide make clear, the situation for selection sort is very different. The table on the right shows the average running time when selection sort is applied to 10, 100, 1000, and 10000 values.
- As a rough approximation—particularly as you work with larger values of N—it appears that every ten-fold increase in the size of the array means that selection sort takes about 100 times as long.

| N | time |
|---|------|
| 10 | .0024 |
| 100 | 0.162 |
| 1000 | 14.32 |
| 10000 | 1332. |

## Counting Operations

- Another way to estimate the running time is to count how many operations are required to sort an array of size N.
- In the selection sort implementation, the section of code that is executed most frequently and therefore contributes the most to the running time is the body of the `findSmallest` method. The number of operations involved in each call to `findSmallest` changes as the algorithm proceeds:
  - N values are considered on the first call to `findSmallest`.
  - N − 1 values are considered on the second call.
  - N − 2 values are considered on the third call, and so on.
- In mathematical notation, the number of values considered in `findSmallest` can be expressed as a summation, which can then be transformed into a simple formula:
  1 + 2 + 3 + ⋯ + (N − 1) + N = ∑_{i=1}^{N} i = (N × (N + 1)) / 2

## A Geometric Insight

- You can convince yourself that

  1 + 2 + 3 + ⋯ + (N − 2) + (N − 1) + N = \frac{N \times (N + 1)}{2}

  by thinking about the problem geometrically.
- The terms on the left side of the formula can be arranged into a triangle, as shown at the bottom of this slide for N = 6.
- If you duplicate the triangle and rotate it by 180°, you get a rectangle that in this case contains 6 × 7 dots, half of which belong to each triangle.

![](img/af430dff16b82a0fe61ce7dee05dcf9c_290_0.png)

## Quadratic Growth

- The reason behind the rapid growth in the running time of selection sort becomes clear if you make a table showing the value of $\frac{N \times (N + 1)}{2}$ for various values of $N$:
- The growth pattern in the right column is similar to that of the measured running time of the selection sort algorithm. As the value of $N$ increases by a factor of 10, the value of $\frac{N \times (N + 1)}{2}$ increases by a factor of around 100, which is $10^2$. Algorithms whose running times increase in proportion to the square of the problem size are said to be *quadratic*.

| N | $\frac{N \times (N + 1)}{2}$ |
|---|---|
| 10 | 55 |
| 100 | 5050 |
| 1000 | 500,500 |
| 10000 | 50,005,000 |

## Big-O Notation

- The most common way to express computational complexity is to use *big-O notation*, which was introduced by the German mathematician Paul Bachmann in 1892.
- Big-O notation consists of the letter *O* followed by a formula that offers a qualitative assessment of running time as a function of the problem size, traditionally denoted as *N*. For example, the computational complexity of linear search is

  $O(N)$

  and the computational complexity of selection sort is

  $O(N^2)$
- If you read these formulas aloud, you would pronounce them as “big-O of *N*” and “big-O of *N*²” respectively.

## Common Simplifications of Big-O

- Given that big-O notation is designed to provide a qualitative assessment, it is important to make the formula inside the parentheses as simple as possible.
- When you write a big-O expression, you should always make the following simplifications:
  1. Eliminate any term whose contribution to the running time ceases to be significant as N becomes large.
  2. Eliminate any constant factors.
- The computational complexity of selection sort is therefore

  $O(N^2)$

  and not

  $O\left(\frac{N \times (N+1)}{2}\right)$

![](img/af430dff16b82a0fe61ce7dee05dcf9c_293_0.png)
