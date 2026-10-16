

## 2.3.1 分治法

- **MERGE(A,p,q,r):** MERGE 排序算法的关键操作，在“合并”步骤中合并两个已排序序列。
  - *A* 是一个数组，*p, q,* 和 *r* 是对数组元素进行编号的下标，且满足 *p ≤ q < r*。
  - 该过程假设子数组 *A[p .. q]* 和 *A[q+1 .. r]* 已按排序顺序排列。该过程将它们合并形成一个单一的已排序子数组，用以替换当前子数组 *A[p .. r]*。
  - 工作步骤：

该过程耗时 Θ(n)，n=r-p+1

? 

9 10 J Q K

7 8 9 10 J

```
MERGE(A, p, q, r)
1   n₁ ← q-p+1
2   n₂ ← r-q
3   create arrays L[1 .. n₁+1] and R[1 .. n₂+1]
4   for i←1 to n₁
5       do L[i]←A[p+i-1]
6   for j←1 to n₂
7       do R[j]←A[q+j]
8   L[n₁+1]←∞    // To avoid having to check whether either pile is empty in each
9   R[n₂+1]←∞    // basic step, a sentinel card is put on the bottom of each pile.
10  i←1
11  j←1
12  for k←p to r
13      do if L[i]≤R[j]
14          then A[k]←L[i]
15              i←i+1
16          else A[k]←R[j]
17              j←j+1
```

![](img/09c68ab421cfce4995ddad1430ef2637_55_0.png)

子程序如何工作？下一页

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

![](img/09c68ab421cfce4995ddad1430ef2637_56_0.png)

### MERGE 的循环不变式性质

```
MERGE(A, p, q, r)
1    n₁ ← q-p+1
2    n₂ ← r-q
3    create L[1 .. n₁+1], R[1 .. n₂+1]
4    for i←1 to n₁
5      do L[i]←A[p+i-1]
6    for j←1 to n₂
7      do R[j]←A[q+j]
8    L[n₁+1]←∞
9    R[n₂+1]←∞
10   i←1
11   j←1
12   for k←p to r
13     do if L[i]≤R[j]
14         then A[k]←L[i]
15              i←i+1
16         else A[k]←R[j]
17              j←j+1
```

初始化：在循环的第一次迭代之前，k = p，因此 A[p .. k-1] 为空。A[p .. k-1] 包含 L 和 R 的 0 个最小元素，并且由于 i=j=1，L[i] 和 R[j] 分别是尚未复制回 A 的各自数组的最小元素。

维护：首先假设 L[i]≤R[j]。由于 A[p .. k-1] 包含 k-p 个最小元素，在第 14 行将 L[i] 复制到 A[k] 之后，子数组 A[p .. k] 将包含 k-p+1 个最小元素。如果 L[i]>R[j]，则如此做。

终止：k=r+1，子数组 A[p .. k-1] 为 A[p .. r]，包含 L[1 .. n₁+1] 和 R[1 .. n₂+1] 的 r-p+1 个最小元素，按排序顺序排列。除了两个最大的哨兵之外，其余元素都已复制回 A。

| MERGE(A, p, q, r) | cost | times |
|---|---|---|
| 1   n₁ ← q-p+1 | c | 1 |
| 2   n₂ ← r-q | c | 1 |
| 3   create arrays L[1 .. n₁+1] and R[1 .. n₂+1] | c | 1 |
| 4   for i←1 to n₁ | c | n₁+1 |
| 5     do L[i]←A[p+i-1] | c | n₁ |
| 6   for j←1 to n₂ | c | n₂+1 |
| 7     do R[j]←A[q+j] | c | n₂ |
| 8   L[n₁+1]←∞ | c | 1 |
| 9   R[n₂+1]←∞ | c | 1 |
| 10  i←1 | c | 1 |
| 11  j←1 | c | 1 |
| 12  for k←p to r | c | r-p+2 |
| 13    do if L[i]≤R[j] | c | r-p+1 |
| 14      then A[k]←L[i] | c | x |
| 15        i←i+1 | c | x |
| 16      else A[k]←R[j] | c | r-p+1-x |
| 17        j←j+1 | c | r-p+1-x |

r-p+1
= n₁ + n₂ = n

1<=x<=n₁

Θ(n₁+n₂)=Θ(n)

- MERGE 过程作为子程序。
- MERGE-SORT(A, p, r) 对子数组 A[p .. r] 中的元素进行排序。
- 如果 p ≥ r，则子数组最多有一个元素，已排序，为基本情况。
- 否则，分治步骤计算一个下标 q，将 A[p .. r] 分区为两个子数组：A[p .. q]，包含 ⌊n/2⌋ 个元素，和 A[q+1 .. r]，包含 ⌈n/2⌉ 个元素。

```
MERGE-SORT(A, p, r)
1  if p < r
2    Then q ← ⌊(p+r)/2⌋
3      MERGE-SORT(A, p, q)
4      MERGE-SORT(A, q+1, r)
5      MERGE(A, p, q, r)
```

