# 5.3.2 Randomly permuting an array

# (2) RANDOMIZE-IN-PLACE

```
RANDOMIZE-IN-PLACE(A, n)
for(i=1; i<=n; i++)
    swap(A[i], A[RANDOM(i, n)])
```

Lemma RANDOMIZE-IN-PLACE computes a uniform random permutation.

Proof Loop invariant: Pr{A[1 .. i-1] contains each (i-1)-permutation} = (n-i+1)!/n! .

+   - Maintenance: Assume that prior to the ith iteration, Pr{A[1 .. i-1] contains each (i-1)-permutation} = (n-i+1)!/n! , we will show that after the ith iteration, Pr(A[1 .. i] contains each i-permutation) = (n-i)!/n! .
+     （第 i 次迭代前，设(i-1)-置换 A[1 .. i-1] 中，任一置换发生的概率为 (n-i+1)!/n! ，则需证明在第 i 次迭代后，任一 i 置换的概率为(n-i)!/n! ）

Consider a particular i-permutation R=<x₁, x₂, ..., xᵢ>. It consists of an (i-1)-permutation R’=<x₁, x₂, ..., xᵢ₋₁>, followed by xᵢ. （考虑一个特别的 i-置换 R，其前 i-1 个元素组成 (i-1)-置换 R’，最后一个元素为 xᵢ）。……