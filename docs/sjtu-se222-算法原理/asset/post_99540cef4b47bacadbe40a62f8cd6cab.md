
## Dijkstra's algorithm
- Consider vertices in increasing order of distance from *s* (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_706_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 20.0 | 1→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 26.0 | 5→6 |
| 7 | 8.0 | 0→7 |

select vertex 2

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from s
  (non-tree vertex with the lowest distTo[] value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_707_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 20.0 | 1→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 26.0 | 5→6 |
| 7 | 8.0 | 0→7 |

relax all edges incident from 2

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from $s$ (non-tree vertex with the lowest distTo[] value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_708_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

relax all edges incident from 2

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from s
  (non-tree vertex with the lowest distTo[] value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_709_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from *s* (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_710_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

select vertex 3

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from *s* (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_711_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

relax all edges incident from 3

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from *s* (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_712_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

relax all edges incident from 3

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from *s* (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_713_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

## Dijkstra's algorithm
- Consider vertices in increasing order of distance from s
  (non-tree vertex with the lowest distTo[] value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_715_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 14.0 | 5→2 |
| 3 | 17.0 | 2→3 |
| 4 | 9.0 | 0→4 |
| 5 | 13.0 | 4→5 |
| 6 | 25.0 | 2→6 |
| 7 | 8.0 | 0→7 |

relax all edges incident from 6
