
## Mathematical model

Total running time = sum of cost × frequency for all operations.

- Cost depends on machine, compiler.
- Frequency depends on algorithm, input data.

```
% 1-sum
int count = 0;
for (int i = 0; i < N; i++)
    if (a[i] == 0)
        count++;
```

## Mathematical model

- Relative rather than Absolute.
- Machine independent.
- About large input instance
- **Time complexity** of an algorithm is a function of the size of the input *n*.

## Input size

```
Algorithm 1.9 FIRST
Input: A positive integer n and an array A[1..n] with A[j] = j for 1 ≤ j ≤ n.
Output: ∑_{j=1}^n A[j].
1. sum ← 0;
2. for j ← 1 to n
3.   sum ← sum + A[j]
4. end for
5. return sum
```

```
Algorithm 1.10 SECOND
Input: A positive integer n.
Output: ∑_{j=1}^n j.
1. sum ← 0;
2. for j ← 1 to n
3.   sum ← sum + j
4. end for
5. return sum
```

|  | Algo 1.9 | Algo 1.10 |
|---|---|---|
| input size | n | □log n□ +1 |
| time | n | n |
| relation | Linear | Exponential |

## Input size -- convention

- Sorting and searching: the size of the array
- Graph: the number of the vertices and edges
- Computational geometry: the number points or line segments
- Matrix operation: the dimensions of the input matrices
- Number theory and Cryptography: the number of bits of the input.

## Where are we?

- How to estimate time complexity?
- Analysis of algorithms
  - worst case, best case?
  - Big-O notation

## Searching

**Problem: Searching**  
**Input:** An integer array *A[1...n]*, and an integer *x*  
**Output:** Does *x* exist in *A*?

Does 45 exist in:

9, 8, 9, 6, 2, 56, 12, 5, 4, 30, 67, 93, 25, 44, 96

2, 4, 5, 6, 8, 9, 9, 12, 25, 30, 44, 56, 67, 93, 96

## Linear searching v.s. Binary searching

## Binary searching

2, 4, 5, 6, 8, 9, 9, 12, 25, 30, 44, 56, 67, 93, 96

mid

low

high

```
Algorithm 1.2 BinarySearch
Input: An array A[1..n] of n elements sorted in nondecreasing order and an element x.
Output: j if x = A[j], 1 ≤ j ≤ n, and 0 otherwise.
1. low ← 1; high ← n; j ← 0
2. while low ≤ high and j = 0
3.   mid ← ⌊(low + high)/2⌋
4.   if x = A[mid] then j ← mid
5.   else if x < A[mid] then high ← mid − 1
6.   else low ← mid + 1
7. end while
8. return j
```

## Quiz

|  | Linear Searching | Binary Searching |
|---|---|---|
| Best case |  |  |
| Worst case |  |  |

A. 1    B. logn.    C. n    D. none of above

## Computational Complexity

|  | Linear Searching | Binary Searching |
|---|---|---|
| Worst case | n | log n |

| 10⁻⁶s per instruction | Linear Searching | Binary Searching |
|---|---|---|
| n=1024 | 0.001s | 0.00001s |
| n=2⁴⁰ | 12.7day | 0.00004s |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_58_0.png)

## Where are we?

- How to estimate time complexity?
- Analysis of algorithms
  - worst case, best case?
  - Big-O notation

## Big-O Notation

Definition (O-notation)
Let f(n) and g(n) : ℕ → ℝ⁺ ∪ {0}
    f(n) is said to be O(g(n)), written f(n) = O(g(n)),
    if ∃ c>0. ∃ n₀. ∀ n ≥ n₀. f(n) ≤ c g(n)

- The O-notation provides an upper bound of the running time;
- f grows no faster than some constant times g.

## Big-Ω Notation

Definition (Ω-notation)
Let f(n) and g(n): ℕ → ℝ⁺ ∪ {0}
f(n) is said to be Ω(g(n)), written f(n) = Ω(g(n)), if ∃ c>0, ∃ n₀. ∀ n ≥ n₀, f(n) ≥ c g(n)

- The Ω-notation provides an lower bound of the running time;
- f(n) = O(g(n)) iff g(n) = Ω(f(n)).

## Examples

- log n^k = Ω(log n).
- log n! = Ω(n log n).
- n! = Ω(2^n).
- Searching: T(n) = Ω(1)

Does there exist f,g, such that f = O(g) and f = Ω(g)?

## Big-Θ notation

### Definition (Θ-notation)

f(n)=Θ(g(n)), if both f(n)=O(g(n)) and f(n)=Ω(g(n)).

- log n! = Θ(n log n).
- 10n² + 20 n = Θ(n²)

## Small o-notation

### Definition (o-notation)

Let f(n) and g(n) : ℕ → ℝ⁺ ∪ {0}

f(n) is said to be o(g(n)), written f(n) = o(g(n)), if ∀ c. □ n₀. ∀ n ≥ n₀. f(n) < c g(n)

- log n! = o(n log n)?
- 10n² + 20 n = o(n²)?
- n log n = o(n²)?
