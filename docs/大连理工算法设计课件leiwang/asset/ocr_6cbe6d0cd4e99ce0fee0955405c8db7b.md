# Randomized divide-and-conquer algorithm

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

![](bbox=[0.158, 0.743, 0.847, 0.933])