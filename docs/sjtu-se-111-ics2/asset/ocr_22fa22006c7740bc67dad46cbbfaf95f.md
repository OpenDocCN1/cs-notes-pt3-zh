# Refinement of Graphical Representation

![](bbox=[0.07, 0.24, 0.48, 0.92])

+   - Two chains of data dependencies
+     - Update x by mul
+     - Update i by add
+   - Critical path
+     - Latency of mul is 4
+     - Latency of add is 1

The latency of combine4 is 4

|  | Integer |  | Floating Point |  |  |
|---|---|---|---|---|---|---|
| Function | + | * | + | F* | D* |  |
| combine1 | 12 | 12 | 12 | 12 | 13 |  |
| combine4 | 2 | 3 | 3 | 4 | 5 |  |