# Example of partitioning

6 10 13 5 8 3 2 11

i j

```
x ← A[p]    ▷ pivot = A[p]
i ← p
```

```
do if A[j] ≤ x
then i ← i + 1
exchange A[i] ↔ A[j]
```

x ≤ x ≥ x ?
p i j q