# Summary: Radix Sort

+   - Radix sort:
+     - Assumption: input has *d* digits ranging from 0 to *k*
+     - Basic idea:
+       - Sort elements by digit starting with *least* significant
+       - Use a stable sort (like bucket sort) for each stage
+     - Each pass over *n* numbers with 1 digit takes time O(*n*+*k*), so total time O(*d n*+*d k*)
+       - When *d* is constant and *k*=O(*n*), takes O(*n*) time
+     - Fast, Stable, Simple
+     - Doesn’t sort in place