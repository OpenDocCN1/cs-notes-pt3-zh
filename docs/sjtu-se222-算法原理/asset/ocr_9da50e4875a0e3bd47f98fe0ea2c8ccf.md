# Dijkstra's algorithm

+   - Consider vertices in increasing order of distance from *s* (non-tree vertex with the lowest `distTo[]` value).
+   - Add vertex to tree and relax all edges incident from that vertex.

![](bbox=[0.08, 0.32, 0.68, 0.82])

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 |  |  |
| 3 |  |  |
| 4 | 9.0 | 0→4 |
| 5 |  |  |
| 6 |  |  |
| 7 | 8.0 | 0→7 |

choose vertex 1