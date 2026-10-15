# Breadth-first search

Repeat until queue is empty:

+   - Remove vertex $v$ from queue.
+   - Add to queue all unmarked vertices adjacent to $v$ and mark them.

![](bbox=[0.13, 0.42, 0.64, 0.77])

| queue |
|---|
|  |
| 4 |
| 3 |
| 5 |
| 1 |

| v | edgeTo[v] |
|---|---|
| 0 | - |
| 1 | 0 |
| 2 | 0 |
| 3 | 2 |
| 4 | 2 |
| 5 | 0 |