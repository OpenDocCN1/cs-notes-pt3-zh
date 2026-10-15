
## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_687_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 |  |  |
| 2 |  |  |
| 3 |  |  |
| 4 |  |  |
| 5 |  |  |
| 6 |  |  |
| 7 |  |  |

relax all edges incident from 0

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_688_0.png)

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

relax all edges incident from 0

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_689_0.png)

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

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_690_0.png)

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

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_691_0.png)

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

relax all edges incident from 1

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_692_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 17.0 | 1→2 |
| 3 | 20.0 | 1→3 |
| 4 | 9.0 | 0→4 |
| 5 |  |  |
| 6 |  |  |
| 7 | 8.0 | 0→7 |

relax all edges incident from 1

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_693_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 17.0 | 1→2 |
| 3 | 20.0 | 1→3 |
| 4 | 9.0 | 0→4 |
| 5 |  |  |
| 6 |  |  |
| 7 | 8.0 | 0→7 |

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_694_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 17.0 | 1→2 |
| 3 | 20.0 | 1→3 |
| 4 | 9.0 | 0→4 |
| 5 |  |  |
| 6 |  |  |
| 7 | 8.0 | 0→7 |

choose vertex 7

## Dijkstra's algorithm

- Consider vertices in increasing order of distance from s (non-tree vertex with the lowest `distTo[]` value).
- Add vertex to tree and relax all edges incident from that vertex.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_696_0.png)

| v | distTo[] | edgeTo[] |
|---|---|---|
| 0 | 0.0 | - |
| 1 | 5.0 | 0→1 |
| 2 | 15.0 | 7→2 |
| 3 | 20.0 | 1→3 |
| 4 | 9.0 | 0→4 |
| 5 | 14.0 | 7→5 |
| 6 |  |  |
| 7 | 8.0 | 0→7 |

relax all edges incident from 7
