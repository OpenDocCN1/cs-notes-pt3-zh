# 15.2 Matrix-chain multiplication

+   - First, consider the cost of multiplying two matrices.
+   - Two matrices A and B can be multiplied only if they are compatible: columns of A = rows of B. （仅当矩阵A和B相容时，A和B能相乘）
+     - If A is p×q, B is q×r, then C is p×r.
+     - The time to compute C is dominated by the number of scalar multiplications in line 7, which is pqr. （求得矩阵 C 的计算时间主要由 line7 的标量相乘所决定，相乘次数为pqr）

![](bbox=[0.02, 0.68, 0.42, 0.88])

```
MATRIX-MULTIPLY(A, B)
1 if columns[A] ≠ rows[B]
2   then return "error: incompatible dimensions"
3 else for i ← 1 to rows[A]
4     for j ← 1 to columns[B]
5       C[i,j] ← 0
6       for k ← 1 to columns[A]
7         C[i,j]←C[i,j]+A[i,k]·B[k,j]
8 return C
```