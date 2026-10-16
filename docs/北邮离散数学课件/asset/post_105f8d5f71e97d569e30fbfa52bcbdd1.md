
## Matrix Multiplication Algorithm

- The definition for matrix multiplication can be expressed as an algorithm; **C = AB** where **C** is an *m × n* matrix that is the product of the *m × k* matrix **A** and the *k × n* matrix **B**.
- This algorithm carries out matrix multiplication based on its definition.

```
procedure matrix multiplication(A, B: matrices)
    for i := 1 to m
        for j := 1 to n
            c_ij := 0
            for q := 1 to k
                c_ij := c_ij + a_{iq} b_{qj}
    return C {C = [c_ij] is the product of A and B}

A = [a_ij] is an m × k matrix
B = [b_ij] is a k × n matrix
```

### Complexity of Matrix Multiplication

**Example:** How many additions of integers and multiplications of integers are used by the matrix multiplication algorithm to multiply two $n \times n$ matrices.

**Solution:** There are $n^2$ entries in the product. Finding each entry requires $n$ multiplications and $n - 1$ additions. Hence, $n^3$ multiplications and $n^2(n - 1)$ additions are used.

Hence, the complexity of matrix multiplication is $O(n^3)$.

## Boolean Product Algorithm

- The definition of Boolean product of zero-one matrices can also be converted to an algorithm.

```
procedure Boolean product(A, B: zero-one matrices)
    for i := 1 to m
        for j := 1 to n
            c_ij := 0
            for q := 1 to k
                c_ij := c_ij ∨ (a_{iq} ∧ b_{qj})
    return C {C = [c_ij] is the Boolean product of A and B}
```

### Complexity of Boolean Product Algorithm

**Example:** How many bit operations are used to find $A \odot B$, where $A$ and $B$ are $n \times n$ zero-one matrices?

**Solution:** There are $n^2$ entries in $A \odot B$. A total of $n$ ORs and $n$ ANDs are used to find each entry. Hence, each entry takes $2n$ bit operations. A total of $2n^3$ operations are used.

Therefore the complexity is $O(n^3)$.

## Matrix-Chain Multiplication

How should the matrix-chain $A_1 A_2 \cdots A_n$ be computed using the fewest multiplications of integers, where $A_1, A_2, \dots, A_n$ are $m_1 \times m_2$, $m_2 \times m_3$, $\dots$, $m_n \times m_{n+1}$ integer matrices. Matrix multiplication is associative (exercise in Section 2.6).

**Example:** In which order should the integer matrices $A_1 A_2 A_3$ — where $A_1$ is $30 \times 20$, $A_2$ is $20 \times 40$, and $A_3$ is $40 \times 10$ — be multiplied to use the least number of multiplications?

**Solution:** There are two possible ways to compute $A_1 A_2 A_3$.

- $A_1(A_2A_3)$: $A_2A_3$ takes $20 \cdot 40 \cdot 10 = 8000$ multiplications. Then multiplying $A_1$ by the $20 \times 10$ matrix $A_2A_3$ takes $30 \cdot 20 \cdot 10 = 6000$ multiplications. So the total number is $8000 + 6000 = 14{,}000$.

- $(A_1A_2)A_3$: $A_1A_2$ takes $30 \cdot 20 \cdot 40 = 24{,}000$ multiplications. Then multiplying the $30 \times 40$ matrix $A_1A_2$ by $A_3$ takes $30 \cdot 40 \cdot 10 = 12{,}000$ multiplications. So the total number is $24{,}000 + 12{,}000 = 36{,}000$.

So the first method is best.

An efficient algorithm for finding the best order for matrix-chain multiplication can be based on the algorithmic paradigm known as dynamic programming. (See Ex. 57 in Section 8.1.)

## Algorithmic Paradigms

- An *algorithmic paradigm* is a general approach based on a particular concept for constructing algorithms to solve a variety of problems.
  - Greedy algorithms were introduced in Section 3.1.
  - We discuss brute-force algorithms in this section.
  - We will see divide-and-conquer algorithms (Chapter 8), dynamic programming (Chapter 8), backtracking (Chapter 11), and probabilistic algorithms (Chapter 7). There are many other paradigms that you may see in later courses.

### Brute-Force Algorithms

- A *brute-force algorithm* solves a problem in the most straightforward manner, without taking advantage of any ideas that can make the algorithm more efficient.
- Brute-force algorithms we have previously seen are sequential search, bubble sort, and insertion sort.

![](img/c25dfd82fc242c2db53bc942dcad6885_2280_0.png)

### Computing the Closest Pair of Points by Brute-Force

- Algorithm for finding the closest pair in a set of $n$ points.

```
procedure closest pair((x_1, y_1), (x_2, y_2), …, (x_n, y_n): x_i, y_i real numbers)
    min = ∞
    for i := 1 to n
        for j := 1 to i - 1
            if (x_j - x_i)^2 + (y_j - y_i)^2 < min
            then
                min := (x_j - x_i)^2 + (y_j - y_i)^2
                closest pair := (x_i, y_i), (x_j, y_j)
    return closest pair
```

- The algorithm loops through $n(n-1)/2$ pairs of points, computes the value $(x_j - x_i)^2 + (y_j - y_i)^2$ and compares it with the minimum, etc. So, the algorithm uses $\Theta(n^2)$ arithmetic and comparison operations.

- We will develop an algorithm with $O(n \log n)$ worst-case complexity in Section 8.3.
