# # Unrolling & Accumulating

# ## Idea

+   - Can unroll to any degree L
+   - Can accumulate K results in parallel
+   - L must be multiple of K

# ## Limitations

+   - Diminishing returns
+     - Cannot go beyond throughput limitations of execution units
+   - Large overhead for short lengths
+     - Finish off iterations sequentially