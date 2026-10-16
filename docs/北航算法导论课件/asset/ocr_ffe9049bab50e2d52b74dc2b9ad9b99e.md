# 2.2.1 Analysis of insertion sort

T(n) = c₁n + c₂(n−1) + c₄(n−1) + c₅ Σ_{j=2}^{n} t_j + c₆ Σ_{j=2}^{n} (t_j −1) + c₇ Σ_{j=2}^{n} (t_j −1) + c₈(n−1)

+   An algorithm’s running time may depend on factual input.

+   The worst case results if the array is in reverse sorted order. We must compare each element A[j] with each element in the entire sorted subarray A[1 .. j−1], and so t_j = j.

Σ_{j=2}^{n} j = n(n+1)/2 − 1 ,   Σ_{j=2}^{n} (j−1) = n(n−1)/2

then T(n) = c₁n + c₂(n−1) + c₄(n−1) + c₅( n(n+1)/2 −1 ) + c₆( n(n−1)/2 ) + c₇( n(n−1)/2 ) + c₈(n−1) = a n² + b n + c

It is thus a quadratic function (n²) of n.