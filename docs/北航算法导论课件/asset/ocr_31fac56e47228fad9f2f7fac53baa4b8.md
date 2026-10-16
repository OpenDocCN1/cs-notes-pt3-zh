# 15.2 Matrix-chain multiplication

+   - For A<sub>p×q</sub>, B<sub>q×r</sub>, C=AB is p×r. The # of scalar multiplications is pqr.
+   - Consider the problem of a chain <A₁, A₂, A₃>.
+   - Suppose that A₁: 10×100; A₂: 100×5; A₃: 5×50
+     - If A = ((A₁A₂)A₃),
+       a) C = A₁A₂, # of multiplications 10·100·5 = 5000, C₁₀×5
+       b) A = CA₃, # of multiplications 10·5·50 = 2500, A₁₀×50
+       then, # of scalar multiplications, for a total of 7500.
+     - If A = (A₁(A₂A₃)),
+       a) C₁₀₀×₅₀ = A₂A₃, # of multiplications 100·5·50 = 25,000,
+       b) A₁₀×₅₀ = A₁C, # of multiplications 10·100·50 = 50,000,
+       then, # of scalar multiplications, for a total of 75,000.
+     - The first case is 10 times faster than the second.