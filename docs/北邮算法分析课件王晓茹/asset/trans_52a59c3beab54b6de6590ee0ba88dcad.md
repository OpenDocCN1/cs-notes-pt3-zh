

## 最坏情况递归树

T(n) = T(0) + T(n-1) + cn

cn
T(0) c(n-1)
T(0) c(n-2)
T(0) ...
Θ(1)

Θ(∑k=1n k) = Θ(n2)

T(n) = Θ(n) + Θ(n²)
= Θ(n²)

Θ(∑_{k=1}^n k) = Θ(n²)

![](img/18fa867d493fcce0c8a4a563c309db0a_203_0.png)

## 最佳情况分析
### （仅用于直觉！）

如果我们幸运的话，PARTITION 会将数组均匀地划分：

$T(n) = 2T(n/2) + \Theta(n)$

$= \Theta(n \lg n) \qquad \text{(same as merge sort)}$

如果划分总是 $\frac{1}{10}:\frac{9}{10}$ 呢？

$T(n) = T(\frac{1}{10}n) + T(\frac{9}{10}n) + \Theta(n)$

这个递推式的解是什么？

## “接近最佳”情况的分析

T(n)

![](img/18fa867d493fcce0c8a4a563c309db0a_206_0.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_207_0.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_208_0.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_209_0.png)

![](img/18fa867d493fcce0c8a4a563c309db0a_210_0.png)

## 更多直觉

假设我们交替出现幸运、不幸、幸运、不幸、幸运、....

L(n) = 2U(n/2) + Θ(n) lucky
U(n) = L(n − 1) + Θ(n) unlucky

求解：

L(n) = 2(L(n/2 − 1) + Θ(n/2)) + Θ(n)
= 2L(n/2 − 1) + Θ(n)
= Θ(n lg n) Lucky!

我们如何确保通常是幸运的？

## 快速排序

可以看出： 快速排序算法的性能取决于划分的对称性。
通过修改算法partition， 可以设计出采用随机选择策略

- 最坏时间复杂度： O(n²)
- 平均时间复杂度： O(nlogn)
- 稳定性： 不稳定

```
```java
private static int randomizedPartition (int p, int r)
{
    int i = random(p,r);
    MyMath.swap(a, i, p);
    return partition (p, r);
}
```
```

## Randomized quicksort

**IDEA**: Partition around a _random_ element.

- Running time is independent of the input order.
- No assumptions need to be made about the input distribution.
- No specific input elicits the worst-case behavior.
- The worst case is determined only by the output of a random-number generator.

## Randomized quicksort analysis

Let \( T(n) = \) the random variable for the running time of randomized quicksort on an input of size \( n \), assuming random numbers are independent.

For \( k = 0, 1, \dots, n-1 \), define the **indicator random variable**

\( X_k = \begin{cases} 1 & \text{if PARTITION generates a } k : n-k-1 \text{ split,} \\ 0 & \text{otherwise.} \end{cases} \)

\( E[X_k] = \Pr\{X_k = 1\} = 1/n \), since all splits are equally likely, assuming elements are distinct.

## Analysis (continued)

\( T(n) = \begin{cases} T(0) + T(n-1) + \Theta(n) & \text{if } 0:n-1 \text{ split,} \\ T(1) + T(n-2) + \Theta(n) & \text{if } 1:n-2 \text{ split,} \\ \quad \vdots \\ T(n-1) + T(0) + \Theta(n) & \text{if } n-1:0 \text{ split,} \end{cases} \)

\( = \sum_{k=0}^{n-1} X_k \left( T(k) + T(n-k-1) + \Theta(n) \right). \)

## Calculating expectation

Take expectations of both sides.

```
\( E[T(n)] = E\left[\sum_{k=0}^{n-1} X_k(T(k) + T(n-k-1) + \Theta(n))\right] \)
```

Linearity of expectation.

```
E[T(n)] = E[\sum_{k=0}^{n-1} X_k(T(k) + T(n-k-1) + \Theta(n))]
= \sum_{k=0}^{n-1} E[X_k(T(k) + T(n-k-1) + \Theta(n))]
```

Independence of \(X_k\) from other random choices.

```
\( E[T(n)] = E \left[ \sum_{k=0}^{n-1} X_k (T(k) + T(n-k-1) + \Theta(n)) \right] \\
= \sum_{k=0}^{n-1} E[X_k(T(k) + T(n-k-1) + \Theta(n))] \\
= \sum_{k=0}^{n-1} E[X_k] \cdot E[T(k) + T(n-k-1) + \Theta(n)] \)
```

\(E[T(n)] = E\left[\sum_{k=0}^{n-1} X_k(T(k) + T(n-k-1) + \Theta(n))\right]\)
\(= \sum_{k=0}^{n-1} E[X_k(T(k) + T(n-k-1) + \Theta(n))]\)
\(= \sum_{k=0}^{n-1} E[X_k] \cdot E[T(k) + T(n-k-1) + \Theta(n)]\)
\(= \frac{1}{n} \sum_{k=0}^{n-1} E[T(k)] + \frac{1}{n} \sum_{k=0}^{n-1} E[T(n-k-1)] + \frac{1}{n} \sum_{k=0}^{n-1} \Theta(n)\)

Linearity of expectation; \(E[X_k] = 1/n\) .

