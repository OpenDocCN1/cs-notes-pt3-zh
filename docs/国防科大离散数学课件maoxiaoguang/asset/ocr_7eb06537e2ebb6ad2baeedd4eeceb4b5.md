# Set Equality, Subsets

Two sets are equal if they have same elements

+   - {1, 2, 3, 4, 5} = {5, 4, 3, 2, 1}
+   - {1, 2, 3, 2, 4, 3, 2, 1} = {4, 3, 2, 1}
+   - Two sets are not equal if they do not have same elements
+     - {1, 2, 3, 4, 5} ≠ {1, 2, 3, 4}

```
S = T ↔ ∀x (x ∈ S ↔ x ∈ T)
```

If all elements of a set S are also elements of a set T, then S is a subset of T

+   - If S = {2, 4, 6}, T = {1, 2, 3, 4, 5, 6, 7}, S is a subset of T
+   - This is specified by S ⊆ T meaning that ∀ x (x ∈ S → x ∈ T)

```
S ⊆ T ↔ ∀x (x ∈ S → x ∈ T)
```