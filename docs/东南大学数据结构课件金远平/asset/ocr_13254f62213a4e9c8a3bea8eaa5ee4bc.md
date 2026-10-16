# Proof:

In the call to QuickSort(a, 1, n), the pivot gets place at position j, we need to sort 2 sublists of size j-1 and n-j. j may take on any of the 1 to n with equal probability, so

T_avg(n) ≤ cn + (1/n) Σ_{j=1}^{n} (T_avg(j-1) + T_avg(n-j))

= cn + (2/n) Σ_{j=0}^{n-1} T_avg(j), n ≥ 2 --- (7.1)