

## 2.3.1 分治法

```
MERGE(A, p, q, r)
1   n₁ ← q-p+1
2   n₂ ← r-q
3   create arrays L[1 .. n₁+1] and R[1 .. n₂+1]
4   for i←1 to n₁
5       do L[i]←A[p+i-1]
6   for j←1 to n₂
7       do R[j]←A[q+j]
8   L[n₁+1]←∞
9   R[n₂+1]←∞
10  i←1
11  j←1
12  for k←p to r
13      do if L[i]≤R[j]
14          then A[k]←L[i]
15              i←i+1
16          else A[k]←R[j]
17              j←j+1
```

![](img/09c68ab421cfce4995ddad1430ef2637_91_0.png)

### MERGE 循环不变式的性质

初始化：在循环第一次迭代之前，k = p，因此 A[p .. k-1] 是空的。A[p .. k-1] 包含 L 和 R 的 0 个最小元素，且由于 i = j = 1，L[i] 和 R[j] 分别是各自数组中尚未复制回 A 的最小元素。

保持：首先假设 L[i] ≤ R[j]。因为 A[p .. k-1] 包含 k-p 个最小元素，在第 14 行将 L[i] 复制到 A[k] 之后，子数组 A[p .. k] 将包含 k-p+1 个最小元素。如果 L[i] > R[j]，则第 16-17 行执行适当的操作以维持循环不变式。

终止：终止时，k = r + 1。子数组 A[p .. k-1] 就是 A[p .. r]，它按排序顺序包含 L[1 .. n₁+1] 和 R[1 .. n₂+1] 的 r-p+1 个最小元素。除两个最大的元素（哨兵）之外，所有元素都已复制回 A。

| MERGE(A, p, q, r) | 代价 | 次数 |
|---|---|---|
| 1 n₁ ← q-p+1 | c | 1 |
| 2 n₂ ← r-q | c | 1 |
| 3 创建数组 L[1 .. n₁+1] 和 R[1 .. n₂+1] | c | 1 |
| 4 对于 i←1 到 n₁ | c | n₁+1 |
| 5 执行 L[i]←A[p+i-1] | c | n₁ |
| 6 对于 j←1 到 n₂ | c | n₂+1 |
| 7 执行 R[j]←A[q+j] | c | n₂ |
| 8 L[n₁+1]←∞ | c | 1 |
| 9 R[n₂+1]←∞ | c | 1 |
| 10 i←1 | c | 1 |
| 11 j←1 | c | 1 |
| 12 对于 k←p 到 r | c | r-p+2 |
| 13 执行：如果 L[i]≤R[j] | c | r-p+1 |
| 14 那么 A[k]←L[i] | c | x |
| 15 i←i+1 | c | x |
| 16 否则 A[k]←R[j] | c | r-p+1-x |
| 17 j←j+1 | c | r-p+1-x |

```
r-p+1
= n₁ + n₂ = n

1 ≤ x ≤ n₁

Θ(n₁+n₂) = Θ(n)
```

- MERGE 过程作为一个子程序。
- MERGE-SORT(A, p, r) 对子数组 A[p .. r] 中的元素进行排序。
- 如果 p ≥ r，子数组至多只有一个元素，已经有序，这是基本情况。
- 否则，分解步骤计算一个下标 q，将 A[p .. r] 划分为两个子数组：A[p .. q] 包含 ⌊n/2⌋ 个元素，A[q+1 .. r] 包含 ⌈n/2⌉ 个元素。

```
MERGE-SORT(A, p, r)
1  if p < r
2    then q ← ⌊(p+r)/2⌋
3    MERGE-SORT(A, p, q)
4    MERGE-SORT(A, q+1, r)
5    MERGE(A, p, q, r)
```

![](img/09c68ab421cfce4995ddad1430ef2637_95_0.png)

![](img/09c68ab421cfce4995ddad1430ef2637_95_1.png)

```
MERGE-SORT(A, 1, 4)
1  if 1 < 4
2    then q ← ⌊(1 + 4) / 2⌋ = 2
3    MERGE-SORT(A, 1, 2)
1  if 1 < 2
2    then q ← ⌊(1 + 2) / 2⌋ = 1
3    MERGE-SORT(A, 1, 1)
1  if 1 < 1
4    MERGE-SORT(A, 2, 2)
1  if 2 < 2
5    MERGE(A, 1, 1, 2)
4    MERGE-SORT(A, 3, 4)
1  if 3 < 4
2    then q ← ⌊(3 + 4) / 2⌋ = 3
3    MERGE-SORT(A, 3, 3)
1  if 3 < 3
4    MERGE-SORT(A, 4, 4)
1  if 4 < 4
5    MERGE(A, 3, 3, 4)
5    MERGE(A, 1, 2, 4)
```

