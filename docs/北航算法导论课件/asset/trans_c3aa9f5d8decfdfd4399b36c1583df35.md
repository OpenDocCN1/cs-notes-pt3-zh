

## 2.3.1 分治法

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

## 2.3.2 分析分治算法

当一个算法包含对自身的递归调用时，其运行时间通常可以用递归方程或递归式来描述，该方程根据规模更小的输入上的运行时间来描述规模为 n 的问题的总运行时间。

我们得到如下递归式：

T(n) = { Θ(1) 若 n ≤ c
         aT(n / b) + D(n) + C(n) 否则 }

- D(n) 是将问题分解为子问题所需的时间。
- C(n) 是将子问题的解合并为原问题的解所需的时间。

```
MERGE-SORT(A, p, r)
1   if p < r
2     Then q ← ⌊(p + r) / 2⌋
3       MERGE-SORT(A, p, q)
4       MERGE-SORT(A, q+1, r)
5       MERGE(A, p, q, r)
```

T(n) = { Θ(1) 若 n ≤ c
         a T(n / b) + D(n) + C(n) 否则 }

- 假设原问题规模是 2 的幂，可以简化递归式的分析。这样，每一次分解都会得到两个规模恰好为 n/2 的子序列（该假设不影响递归式解的增长阶）。

```
MERGE-SORT(A, p, r)
1   if p < r
2   Then q ← ⌊(p + r) / 2⌋
3       MERGE-SORT(A, p, q)
4       MERGE-SORT(A, q + 1, r)
5       MERGE(A, p, q, r)
```

T(n) = { Θ(1) 若 n ≤ c
          aT(n / b) + D(n) + C(n) 否则 }

如何为 T(n)（归并排序对 n 个数的最坏情况运行时间）建立递归式？

- 如果只有一个元素 n=1，则需要常数时间。
- 当 n>1 时，

- **分解**：该步骤只是计算子数组的中间位置，只需一步。因此，D(n)=Θ(1)。
- **解决**：递归求解两个规模均为 n/2 的子问题，它对运行时间的贡献为 2T(n/2)。
- **合并**：MERGE 过程表明 C(n)=Θ(n)。

T(n) = { Θ(1) 若 n = 1
         2T(n / 2) + Θ(n) 若 n > 1 }

```
MERGE-SORT(A, p, r)
1   if p < r
2       Then q ← ⌊(p + r) / 2⌋
3           MERGE-SORT(A, p, q)
4           MERGE-SORT(A, q+1, r)
5           MERGE(A, p, q, r)
```

重写递归方程：

T(n) = { Θ(1)          若 n = 1
         2T(n/2) + Θ(n)  若 n > 1 }

T(n) = { Θ(1)          若 n = 1
         2T(n/2) + c n   若 n > 1 }

求解该递归方程。

![](img/09c68ab421cfce4995ddad1430ef2637_64_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_65_0.png)

将所有层的代价相加。共有 lg n + 1 层，每层代价为 cn，因此总代价为

cn(lg n + 1) = cn lg n + cn = Θ(n lg n)

显然，对于足够大的输入规模，它在最坏情况下的性能优于插入排序，插入排序的运行时间为 Θ(n²)。

## 练习与问题

## 练习

分析 Fibonacci 序列 F(n) = F(n-1) + F(n-2) 的如下算法的时间复杂度。

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

- 练习

全部

补充：自己编程实现几种常用的排序算法（插入、冒泡、归并、快排、等等），并比较分析其运算时间。输入为随机产生的 n 个数，让 n 尽可能大。

- 问题

全部

## 2 入门

目标：

- 开始使用描述和分析算法的框架
- 考察两种排序算法：插入排序和归并排序
- 学习如何用伪代码、C/C++ 描述算法并论证其正确性
- 开始使用渐近记号来表示运行时间分析
- 在归并排序的背景下学习“分而治之”的技术

