# (2) The optimal case

2 sublists with equal size, roughly n/2.

T_opt(n) ≤ cn + 2T_opt(n/2)

≤ cn + 2(cn/2 + 2T_opt(n/4)

≤ 2cn + 4T_opt(n/4)

...

≤ cn log₂ n + n T_opt(1) = O(n log n).

# (3) The average time

Lemma 7.1: T_avg(n) ≤ k* n logₑ n for n ≥ 2.