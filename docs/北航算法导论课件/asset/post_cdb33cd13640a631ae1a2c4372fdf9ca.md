
## 2.3.1 The divide-and-conquer approach

```
MERGE-SORT(A, p, r)
1  if p < r
2    Then q ← ⌊(p + r)/2⌋
3      MERGE-SORT(A, p, q)
4      MERGE-SORT(A, q+1, r)
5      MERGE(A, p, q, r)
```

![](img/09c68ab421cfce4995ddad1430ef2637_60_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_60_1.png)

```
MERGE-SORT(A, 1, 4)
1 if 1 < 4
2   Then q ← ⌊(1 + 4)/2⌋ = 2
3   MERGE-SORT(A, 1, 2)
1 if 1 < 2
2 Then q ← ⌊(1 + 2)/2⌋ = 1
3 MERGE-SORT(A, 1, 1)
1 if 1 < 1
4 MERGE-SORT(A, 2, 2)
1 if 2 < 2
5 MERGE(A, 1, 1, 2)
4 MERGE-SORT(A, 3, 4)
1 if 3 < 4
2 Then q ← ⌊(3 + 4)/2⌋ = 3
3 MERGE-SORT(A, 3, 3)
1 if 3 < 3
4 MERGE-SORT(A, 4, 4)
1 if 4 < 4
5 MERGE(A, 3, 3, 4)
MERGE(A, 1, 2, 4)
```

## 2.3.2 Analyzing divide-and-conquer algorithms

When an algorithm contains a recursive call to itself, its running time can often be described by a recurrence equation or recurrence, which described the overall running time on a problem of size n in terms of the running time on smaller inputs.

We get the recurrence

T(n) = { Θ(1) if n ≤ c
 aT(n / b) + D(n) + C(n) otherwise }

- D(n) is the time of dividing the problem into subproblems.
- C(n) is the time of combining the solutions to the subproblems into the solution to the original problem.

```
MERGE-SORT(A, p, r)
1   if p < r
2     Then q ← ⌊(p + r) / 2⌋
3       MERGE-SORT(A, p, q)
4       MERGE-SORT(A, q+1, r)
5       MERGE(A, p, q, r)
```

T(n) = { Θ(1) if n ≤ c
 a T(n / b) + D(n) + C(n) otherwise }

- Assume that the original problem size is a power of 2, the recurrence analysis is simplified. Each divide step then yields two subsequences of size exactly n/2 (the assumption does not affect the order of growth of the solution to the recurrence).

```
MERGE-SORT(A, p, r)
1   if p < r
2   Then q ← ⌊(p + r) / 2⌋
3       MERGE-SORT(A, p, q)
4       MERGE-SORT(A, q + 1, r)
5       MERGE(A, p, q, r)
```

T(n) = { Θ(1) if n ≤ c
  aT(n / b) + D(n) + C(n) otherwise }

How to set up the recurrence for T(n), the worst-case running time of merge sort on n numbers?

- If one element n=1, takes constant time.
- When n>1,

- **Divide**: The step just computes the middle of the subarray, one step. Thus, D(n)=Θ(1).
- **Conquer**: Recursively solve two subprolems, each of size n/2, which contributes 2T(n/2) to the running time.
- **Combine**: MERGE procedure shows C(n)=Θ(n).

T(n) = { Θ(1) if n = 1
  2T(n / 2) + Θ(n) if n > 1 }

```
MERGE-SORT(A, p, r)
1   if p < r
2       Then q ← ⌊(p + r) / 2⌋
3           MERGE-SORT(A, p, q)
4           MERGE-SORT(A, q+1, r)
5           MERGE(A, p, q, r)
```

Rewrite the recurrence equation

T(n) = { Θ(1)          if n = 1
        2T(n/2) + Θ(n)  if n > 1 }

T(n) = { Θ(1)          if n = 1
        2T(n/2) + c n   if n > 1 }

solve the recurrence equation.

![](img/09c68ab421cfce4995ddad1430ef2637_64_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_65_0.png)

Add up the costs of all the levels.
There are lg n + 1 levels, each costing cn, for a total cost

cn(lg n + 1) = cn lg n + cn = Θ(n lg n)

obviously, it outperforms insertion sort, whose running time is Θ(n²), in the worst case, for large enough inputs.

## Exercises and problems

## Exercises

分析Fibonacci序列 F(n) = F(n-1) + F(n-2) 如下算法的时间复杂度。

```
re_type f(type n)
{
    if(n<=2)
        return 1;
    else
        return f(n-1)+f(n-2);
}
```

```
f1 = 1;
f2 = 1;

for(i=3; i<=n; i++){
    f = f1 + f2;
    f1 = f2;
    f2 = f;
}
```

- Exercises

All

补充：自己编程实现几种常用的排序算法（插入、冒泡、归并、快排、等等），并比较分析其运算时间。输入为随机产生的n个数，让n尽可能地大。

- Problems

All

## 2 Getting Started

Goals:

- Start using framework for describing and analyzing algorithms （描述和分析算法的框架）
- Examine two algorithms for sorting: insertion sort and merge sort
- See how to describe algorithms in pseudocode, C/C++ and argue the correctness of that （如何描述算法）
- Begin using asymptotic notation to express running-time analysis （使用一致性符号来分析算法的运算时间）
- Learn the technique of “divide and conquer” in the context of merge sort （通过merge sort来学习分而治之方法）
