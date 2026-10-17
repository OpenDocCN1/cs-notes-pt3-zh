![](bbox=[0.02, 0.02, 0.22, 0.15])

# Memoization algorithm

Memoization: After computing a solution to a subproblem, store it in a table. Subsequent calls check the table to avoid redoing work.

```
LCS(x, y, i, j)

if c[i,j] = NIL
then if x[i] = y[j]
then c[i,j] ← LCS(x, y, i-1, j-1) + 1
else c[i,j] ← max { LCS(x, y, i-1, j),
LCS(x, y, i, j-1)}
```

Time = Θ(mn) = constant work per table entry.

Space = Θ(mn).

same as before