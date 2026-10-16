# Other Relational Operations (Cont.)

+   - Duplicate elimination
+     - Perform by using either of the parallel sort techniques
+       - eliminate duplicates as soon as they are found during sorting.
+     - Can also partition the tuples (using either range- or hash-partitioning) and perform duplicate elimination locally at each processor.
+   - Projection
+     - Projection without duplicate elimination can be performed as tuples are read in from disk in parallel.
+     - If duplicate elimination is required, any of the above duplicate elimination techniques can be used.