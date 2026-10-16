# External Sort-Merge (Cont.)

+   - If $N \ge M$, several merge *passes* are required.
+     - In each pass, contiguous groups of $M - 1$ runs are merged.
+     - A pass reduces the number of runs by a factor of $M -1$, and creates runs longer by the same factor.
+       - E.g. If M=11, and there are 90 runs, one pass reduces the number of runs to 9, each 10 times the size of the initial runs
+     - Repeated passes are performed till all runs have been merged into one.