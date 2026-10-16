# Example 1.5 **Permutation Generator**

**Problem:** for a set of n ≥ 1 elements, print all possible permutations of it.

# Solution:

look at (a,b,c), the answer is by printing:

+   1. a followed by all permutations of (b,c)
+   2. b followed by all permutations of (a,c)
+   3. c followed by all permutations of (b,a)