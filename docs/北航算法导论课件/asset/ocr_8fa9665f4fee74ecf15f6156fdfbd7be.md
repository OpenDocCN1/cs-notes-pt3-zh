# 2.3.1 The divide-and-conquer approach

```
MERGE-SORT(A, p, r)
1  if p < r
2    Then q ← ⌊(p + r) / 2⌋
3    MERGE-SORT(A, p, q)
4    MERGE-SORT(A, q + 1, r)
5    MERGE(A, p, q, r)
```

![](bbox=[0.07, 0.58, 0.38, 0.92])

![](bbox=[0.35, 0.55, 0.65, 0.92])

```
MERGE-SORT(A, 1, 4)
1 if 1 < 4
2   Then q ← ⌊(1 + 4) / 2⌋ = 2
3   MERGE-SORT(A, 1, 2)
1 if 1 < 2
2 Then q ← ⌊(1 + 2) / 2⌋ = 1
3 MERGE-SORT(A, 1, 1)
1 if 1 < 1
4 MERGE-SORT(A, 2, 2)
1 if 2 < 2
5 MERGE(A, 1, 1, 2)
4 MERGE-SORT(A, 3, 4)
1 if 3 < 4
2 Then q ← ⌊(3 + 4) / 2⌋ = 3
3 MERGE-SORT(A, 3, 3)
1 if 3 < 3
4 MERGE-SORT(A, 4, 4)
1 if 4 < 4
5 MERGE(A, 3, 3, 4)
5 MERGE(A, 1, 2, 4)
```