# Calculation

# Case 1: i − 1 is an exact power of 2.

ĉᵢ = i + 2 − 2⌈lg i⌉ + 2⌈lg (i−1)⌉
= i + 2 − 2(i − 1) + (i − 1)
= i + 2 − 2i + 2 + i − 1
= 3

# Case 2: i − 1 is not an exact power of 2.

ĉᵢ = 1 + 2 − 2⌈lg i⌉ + 2⌈lg (i−1)⌉
= 3

Therefore, n insertions cost Θ(n) in the worst case.

# Exercise: Fix the bug in this analysis to show that the amortized cost of the first insertion is only 2.