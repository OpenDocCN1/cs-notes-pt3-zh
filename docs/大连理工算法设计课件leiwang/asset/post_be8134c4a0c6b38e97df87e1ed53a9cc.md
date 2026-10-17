

## Randomized divide-and-conquer algorithm

```
RANDOM-SELECT(A, p, q, i) ▷ ith smallest of A[p...q]
    if p = q then return A[p]
    r ← RANDOM-PARTITION(A, p, q)
    k ← r − p + 1 ▷ k = rank(A[r])
    if i = k then return A[r]
    if i < k
        then return RANDOM-SELECT(A, p, r − 1, i)
        else return RANDOM-SELECT(A, r + 1, q, i − k)
```

![](img/5e59105b951890406cf98b2a964cb2f9_378_0.png)

## Example

Select the \( i = 7\)th smallest:

6 10 13 5 8 3 2 11 \( i = 7 \)

**pivot**

Partition:

2 5 3 6 8 13 10 11 \( k = 4 \)

Select the \( 7 - 4 = 3\)rd smallest recursively.

## Intuition for analysis

(All our analyses today assume that all elements are distinct.)

### Lucky:

\( T(n) = T(9n/10) + \Theta(n) \)
\( = \Theta(n) \)

\( n^{\log_{10/9}1} = n^0 = 1 \)
CASE 3

### Unlucky:

\( T(n) = T(n-1) + \Theta(n) \)
\( = \Theta(n^2) \)

arithmetic series

**_Worse than sorting!_**

## Analysis of expected time

The analysis follows that of randomized quicksort, but it’s a little different.

Let _T_(_n_) = the random variable for the running time of RAND-SELECT on an input of size _n_, assuming random numbers are independent.

For _k_ = 0, 1, ..., _n_-1, define the **indicator random variable**

\(X_k = \left\{ \begin{array}{ c c }
1 & \text{if PARTITION generates a } k : n-k-1 \text{ split,} \\
0 & \text{otherwise.}
\end{array}\right.\)

## Analysis (continued)

To obtain an upper bound, assume that the \(i\)th element always falls in the larger side of the partition:

\(T(n) = \left\{\begin{array}{ c c }
T(\max \{0, n-1\}) + \Theta(n) & \text{if } 0:n-1 \text{ split,} \\
T(\max \{1, n-2\}) + \Theta(n) & \text{if } 1:n-2 \text{ split,} \\
\vdots & \\
T(\max \{n-1, 0\}) + \Theta(n) & \text{if } n-1:0 \text{ split,}
\end{array}\right.\)

\(=\sum_{k=0}^{n-1} X_k \left(T(\max \{k, n-k-1\}) + \Theta(n)\right).\)

September 28, 2005 Copyright © 2001-5 by Erik D. Demaine and Charles E. Leiserson L6.7

## Calculating expectation

Take expectations of both sides.

![](img/5e59105b951890406cf98b2a964cb2f9_383_0.png)

```
```
E[T(n)] = E[\sum_{k=0}^{n-1} X_k(T(max{k, n-k-1}) + \Theta(n))]
```
```

## Calculating expectation

E[T(n)] = E\left[ \sum_{k=0}^{n-1} X_k (T(\max \{k, n - k - 1\}) + \Theta(n)) ight]

= \sum_{k=0}^{n-1} E\left[ X_k (T(\max \{k, n - k - 1\}) + \Theta(n)) ight]

Linearity of expectation.

## Calculating expectation

\(E[T(n)] = E\left[\sum_{k=0}^{n-1} X_k(T(\max\{k, n-k-1\}) + \Theta(n))\right]\)
\(= \sum_{k=0}^{n-1} E[X_k(T(\max\{k, n-k-1\}) + \Theta(n))]\)
\(= \sum_{k=0}^{n-1} E[X_k] \cdot E[T(\max\{k, n-k-1\}) + \Theta(n)]\)

Independence of \(X_k\) from other random choices.

## Calculating expectation

$$ET(n)=E\left[\sum_{k=0}^{n-1}X_k\left(T(\max\{k,n-k-1\})+\Theta(n)\right)\right]$$

$$=\sum_{k=0}^{n-1}E\left[X_k\left(T(\max\{k,n-k-1\})+\Theta(n)\right)\right]$$

$$=\sum_{k=0}^{n-1}E[X_k]\cdot E\left[T(\max\{k,n-k-1\})+\Theta(n)\right]$$

$$=\frac{1}{n}\sum_{k=0}^{n-1}E[T(\max\{k,n-k-1\})]+\frac{1}{n}\sum_{k=0}^{n-1}\Theta(n)$$

Linearity of expectation; $E[X_k]=1/n$.

## Calculating expectation

\(E[T(n)] = E\left[\sum_{k=0}^{n-1} X_k(T(\max\{k,n-k-1\}) + \Theta(n))\right]\)
\(= \sum_{k=0}^{n-1} E[X_k(T(\max\{k,n-k-1\}) + \Theta(n))]\)
\(= \sum_{k=0}^{n-1} E[X_k] \cdot E[T(\max\{k,n-k-1\}) + \Theta(n)]\)
\(= \frac{1}{n} \sum_{k=0}^{n-1} E[T(\max\{k,n-k-1\})] + \frac{1}{n} \sum_{k=0}^{n-1} \Theta(n)\)
\(\le \frac{2}{n} \sum_{k=\lfloor n/2 \rfloor}^{n-1} E[T(k)] + \Theta(n)\)

Upper terms appear twice.

## Hairy recurrence

(But not quite as hairy as the quicksort one.)

\(E[T(n)] = \frac{2}{n} \sum_{k=\lfloor n/2 \rfloor}^{n-1} E[T(k)] + \Theta(n)\)

**Prove:** \(E[T(n)] \le cn\) for constant \(c > 0\).

+   • The constant \(c\) can be chosen large enough so that \(E[T(n)] \le cn\) for the base cases.

**Use fact:** \(\sum_{k=\lfloor n/2 \rfloor}^{n-1} k \le \frac{3}{8}n^2\) (exercise).

