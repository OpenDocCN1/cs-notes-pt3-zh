# Materialization (Cont.)

+   - Materialized evaluation is always applicable
+   - Cost of writing results to disk and reading them back can be quite high
+     - Our cost formulas for operations ignore cost of writing results to disk, so
+       - Overall cost = Sum of costs of individual operations + cost of writing intermediate results to disk
+   - Double buffering: use two output buffers for each operation, when one is full write it to disk while the other is getting filled
+     - Allows overlap of disk writes with computation and reduces execution time