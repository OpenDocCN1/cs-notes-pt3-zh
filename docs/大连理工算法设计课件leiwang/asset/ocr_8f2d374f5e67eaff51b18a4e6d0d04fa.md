# # Worst-case recursion tree

T(n) = T(0) + T(n-1) + cn

T(0) cn T(0) c(n-1) T(0) c(n-2) T(0) ... Θ(1)

Θ(∑_{k=1}^n k) = Θ(n^2)