
## Quiz

| f(n) | g(n) |
|------|------|
| n^1.01 | n log² n |
| n log n | log(n!) |
| 1+1/2+1/3+...+1/n | log n |
| n 2^n | 3^n |

A. O    B. Ω.    C. Θ    D. none of above

## Logarithms

log_b xy = log_b x + log_b y

log_b c^y = y log_b c

log_b x = \frac{log_a x}{log_a b}

x^{log_a y} = y^{log_a x}

## Pigeonhole principle

![](img/a8f1b433a70f1e5c410c8b43e41b650e_69_0.png)

(source from wikipedia)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_69_1.png)

Johann Dirichlet

(source from wikipedia)

Prove there exists a number consisting of 7 and 0 that can divide 13.

## Summation

∑_{j=1}^{n} j = n(n + 1)/2 = Θ(n²)

∑_{j=0}^{n} c^{j} = (c^{n+1} - 1)/(c - 1) = Θ(c^{n})

## Approximation by Integration

∫_{m-1}^{n} f(x)dx ≤ ∑_{j=m}^{n} f(j) ≤ ∫_{m}^{n+1} f(x)dx

∫_{m}^{n+1} f(x)dx ≤ ∑_{j=m}^{n} f(j) ≤ ∫_{m-1}^{n} f(x)dx

∑_{j=1}^{n} j^{k} = Θ(n^{k+1})

H_{n} = ∑_{j=1}^{n} 1/j = Θ(ln n) = Θ(log n)

∑_{j=1}^{n} log j = Θ(n log n)

## In terms of limits

Suppose $\lim_{n\to\infty}\frac{f(n)}{g(n)}$ exists

$\lim_{n\to\infty}\frac{f(n)}{g(n)} \neq \infty \quad \text{implies} \quad f(n) = O(g(n))$

$\lim_{n\to\infty}\frac{f(n)}{g(n)} \neq 0 \quad \text{implies} \quad f(n) = \Omega(g(n))$

$\lim_{n\to\infty}\frac{f(n)}{g(n)} = c \quad \text{implies} \quad f(n) = \Theta(g(n))$

$\lim_{n\to\infty}\frac{f(n)}{g(n)} = 0 \quad \text{implies} \quad f(n) = o(g(n))$

$\lim_{n\to\infty}\frac{f(n)}{g(n)} = \infty \quad \text{implies} \quad f(n) = \omega(g(n))$

## Complexity class

### Definition (Complexity class)

An equivalence relation R on the set of complexity functions is defined as follows:

f R g if and only if f(n) = Θ(g(n)).

1 ≺ log log n ≺ log n ≺ √n ≺ n^{3/4} ≺ n ≺ n log n ≺ n² ≺ 2ⁿ ≺ n! ≺ 2^{n²}

## Order of growth

| order | name | example | N = 1000 | N = 2000 |
|---|---|---|---|---|
| 1 | constant | add two numbers | instant | instant |
| log N | logarithmic | binary search | instant | instant |
| N | linear | find the maximum | instant | instant |
| N log N | linearithmic | mergesort | instant | instant |
| N² | quadratic | 2-sum | ~1s | ~2s |
| 2^N | exponential | Hanoi | forever | forever |

Assume the computer consumes 10⁻⁶s per instruction

## Order of growth

![](img/a8f1b433a70f1e5c410c8b43e41b650e_75_0.png)

## Quiz

```
Algorithm 1.7 Count1
Input: n = 2^k, for some positive integer k.
Output: count = number of times Step 4 is executed.
1. count ← 0;
2. while n ≥ 1
3.   for j ← 1 to n
4.     count ← count + 1
5.   end for
6.   n ← n/2
7. end while
8. return count
```

- A. Θ(n²)
- B. Θ(n).
- C. Θ(nlogn)
- D. none of above

## Quiz

Algorithm 1.7 Count1

Input: $n = 2^k$, for some positive integer $k$.

Output: $count$ = number of times Step 4 is executed.

- 1. $count \leftarrow 0$;
- 2. **while** $n \ge 1$
- 3. **for** $j \leftarrow 1$ **to** $n$
- 4. $count \leftarrow count + 1$
- 5. **end for**
- 6. $n \leftarrow n/2$
- 7. **end while**
- 8. **return** $count$

```
$n + \frac{n}{2} + \frac{n}{2^2} + \cdots + \frac{n}{2^j} + \cdots + \frac{n}{2^{\log n}} = 2n - 1 = \theta(n)$
```

## Quiz

Algorithm 1.8 Count2

Input: A positive integer n.

Output: count = number of times Step 5 is executed.

- 1. count ← 0;
- 2. for i ← 1 to n
- 3. m ← ⌊n/i⌋
- 4. for j ← 1 to m
- 5. count ← count + 1
- 6. end for
- 7. end for
- 8. return count

A. Θ(n²)    B. Θ(n).    C. Θ(nlogn)    D. none of above

## Quiz

### Algorithm 1.8 Count2

Input: A positive integer n.

Output: count = number of times Step 5 is executed.

- 1. count ← 0;
- 2. for i ← 1 to n
- 3. m ← ⌊n/i⌋
- 4. for j ← 1 to m
- 5. count ← count + 1
- 6. end for
- 7. end for
- 8. return count

A. Θ(n²)    B. Θ(n).

![](img/a8f1b433a70f1e5c410c8b43e41b650e_79_0.png)

## Quiz

```
Algorithm 1.9 Count3
Input: n = 2^{2^k}, k is a positive integer.
Output: count = number of times Step 6 is executed.

1. count ← 0;
2. for i ← 1 to n
3.     j ← 2;
4.     while j ≤ n
5.         j ← j²;
6.         count ← count + 1
7.     end while
8. end for
9. return count
```

- A. Θ(n²)
- B. Θ(n).
- C. Θ(n log n)
- D. none of above
