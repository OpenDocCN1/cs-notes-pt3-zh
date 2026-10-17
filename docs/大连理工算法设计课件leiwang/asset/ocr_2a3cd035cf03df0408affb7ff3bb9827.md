# # Partitioning subroutine

PARTITION(A, p, q) ▷ A[p .. q]
x ← A[p] ▷ pivot = A[p]
i ← p
for j ← p + 1 to q
do if A[j] ≤ x
then i ← i + 1
exchange A[i] ↔ A[j]
exchange A[p] ↔ A[i]
return i

> Running time
> = O(n) for n
> elements.

# ## Invariant:

![](bbox=[0.283, 0.75, 0.892, 0.904])