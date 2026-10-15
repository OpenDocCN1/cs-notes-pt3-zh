# Dijkstra's algorithm

+   - Consider vertices in increasing order of distance from *s* (non-tree vertex with the lowest `distTo[]` value).
+   - Add vertex to tree and relax all edges incident from that vertex.

![](bbox=[0.07, 0.36, 0.68, 0.84])

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 15.0 | 7→2 |
| 3 | 20.0 | 1→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 29.0 | 4→6 |
| 7 | 8.0 | 0→7 |

select vertex 5