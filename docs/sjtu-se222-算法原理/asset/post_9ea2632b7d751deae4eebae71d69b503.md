
## Bellman-Ford algorithm demo

Repeat $V$ times: relax all $E$ edges.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_676_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_677_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_678_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_679_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_680_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_681_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_682_0.png)
![](img/a8f1b433a70f1e5c410c8b43e41b650e_683_0.png)

| v | distTo[] | edgeTo[] |
|---|---------:|---------|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

**pass 1**

0→1  0→4  0→7  1→2  1→3  1→7  2→3  2→6  3→6  4→5  4→6  4→7  5→2  5→6  7→5  7→2

**pass 2, 3, 4, ... (no further changes)**

0→1  0→4  0→7  1→2  1→3  1→7  2→3  2→6  3→6  4→5  4→6  4→7  5→2  5→6  7→5  7→2

shortest-paths tree from vertex s

## 4.4 Dijkstra's Algorithm Demo

![](img/a8f1b433a70f1e5c410c8b43e41b650e_684_0.png)

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest distTo[] value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_685_0.png)

an edge-weighted digraph

| edge | weight |
|:---|---:|
| 0→1 | 5.0 |
| 0→4 | 9.0 |
| 0→7 | 8.0 |
| 1→2 | 12.0 |
| 1→3 | 15.0 |
| 1→7 | 4.0 |
| 2→3 | 3.0 |
| 2→6 | 11.0 |
| 3→6 | 9.0 |
| 4→5 | 4.0 |
| 4→6 | 20.0 |
| 4→7 | 5.0 |
| 5→2 | 1.0 |
| 5→6 | 13.0 |
| 7→5 | 6.0 |
| 7→2 | 7.0 |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_686_0.png)

| v | distTo[] | edgeTo[] |
|---|---------:|---------|
| 0 | 0.0 | - |
| 1 |  |  |
| 2 |  |  |
| 3 |  |  |
| 4 |  |  |
| 5 |  |  |
| 6 |  |  |
| 7 |  |  |

choose source vertex 0
