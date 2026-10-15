# Breadth-first search

Repeat until queue is empty:

+   - Remove vertex *v* from queue.
+   - Add to queue all unmarked vertices adjacent to *v* and mark them.

![](bbox=[0.14, 0.385, 0.56, 0.735])

| v | edgeTo[v] |
|---|---|
| 0 | — |
| 1 | 0 |
| 2 | 0 |
| 3 | 2 |
| 4 | 2 |
| 5 | 0 |

dequeue 4