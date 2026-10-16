# Factors Limiting Utility of Pipeline Parallelism

+   - Pipeline parallelism is useful since it avoids writing intermediate results to disk
+   - Useful with small number of processors, but does not scale up well with more processors. One reason is that pipeline chains do not attain sufficient length.
+   - Cannot pipeline operators which do not produce output until all inputs have been accessed (e.g., aggregate and sort)
+   - Little speedup is obtained for the frequent cases of skew in which one operator's execution cost is much higher than the others.