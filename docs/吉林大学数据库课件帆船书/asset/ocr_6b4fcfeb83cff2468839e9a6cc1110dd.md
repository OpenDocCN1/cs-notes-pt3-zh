# Dynamic Programming in Optimization

![](bbox=[0.02, 0.02, 0.15, 0.11])

+   • To find best join tree for a set of n relations:

+   • To find best plan for a set S of n relations, consider all possible plans of the form: S₁ ⋈ (S – S₁) where S₁ is any non-empty subset of S.

+   • Recursively compute costs for joining subsets of S to find the cost of each plan. Choose the cheapest of the 2^n – 2 alternatives.

+   • Base case for recursion: single relation access plan

+     • Apply all selections on R_i using best choice of indices on R_i

+   • When plan for any subset is computed, store it and reuse it when it is required again, instead of recomputing it

+     • Dynamic programming