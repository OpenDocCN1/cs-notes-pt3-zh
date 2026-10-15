# Cachegrind

+   - Cache behavior is crucial
+     - L1 misses: ~10 cycles
+     - L2 misses: ~200 cycles
+   - But difficult to predict
+   - Cachegrind gives three outputs:
+     - Total hit/miss counts and ratios (I1, D1, L2)
+     - Per-function hit/miss counts (sorted from most to least)
+     - Per-line hit/miss counts (source code annotations)
+   - Source code annotations are the most useful
+     - Most fine-grained data
+     - Data that programmers can act on to speed up their programs