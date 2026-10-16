# Analysis of Equivalence:

+   - initialization of first and out ---O(n)
+   - Phase 1---O(m+n)
+   - in Phase 2, each node is put onto the stack once, there are only 2m nodes. The for loop is executed n times. ---O(m+n)

Overall time: O(m+n)

Space required is also O(m+n)

Exercises: P215-1