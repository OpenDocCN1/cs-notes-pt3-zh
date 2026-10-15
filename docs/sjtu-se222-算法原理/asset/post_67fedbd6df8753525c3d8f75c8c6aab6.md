
## Depth-first search

To visit a vertex $v$ :

- Mark vertex $v$ as visited.
- Recursively visit all unmarked vertices pointing from $v$.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_461_0.png)

a directed graph

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | F | - |
| 1 | F | - |
| 2 | F | - |
| 3 | F | - |
| 4 | F | - |
| 5 | F | - |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_462_0.png)

visit 0

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | - |
| 1 | F | - |
| 2 | F | - |
| 3 | F | - |
| 4 | F | - |
| 5 | F | - |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_463_0.png)

visit 5

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | - |
| 1 | F | - |
| 2 | F | - |
| 3 | F | - |
| 4 | F | - |
| 5 | T | 0 |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_464_0.png)

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | - |
| 1 | F | - |
| 2 | F | - |
| 3 | F | - |
| 4 | T | 5 |
| 5 | T | 0 |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

visit 4

![](img/a8f1b433a70f1e5c410c8b43e41b650e_465_0.png)

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | - |
| 1 | F | - |
| 2 | F | - |
| 3 | T | 4 |
| 4 | T | 5 |
| 5 | T | 0 |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

visit 3

![](img/a8f1b433a70f1e5c410c8b43e41b650e_466_0.png)

visit 3

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | - |
| 1 | F | - |
| 2 | F | - |
| 3 | T | 4 |
| 4 | T | 5 |
| 5 | T | 0 |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_467_0.png)

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | — |
| 1 | F | — |
| 2 | T | 3 |
| 3 | T | 4 |
| 4 | T | 5 |
| 5 | T | 0 |
| 6 | F | — |
| 7 | F | — |
| 8 | F | — |
| 9 | F | — |
| 10 | F | — |
| 11 | F | — |
| 12 | F | — |

visit 2

![](img/a8f1b433a70f1e5c410c8b43e41b650e_468_0.png)

visit 2

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | - |
| 1 | F | - |
| 2 | T | 3 |
| 3 | T | 4 |
| 4 | T | 5 |
| 5 | T | 0 |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_469_0.png)

done 2

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | - |
| 1 | F | - |
| 2 | T | 3 |
| 3 | T | 4 |
| 4 | T | 5 |
| 5 | T | 0 |
| 6 | F | - |
| 7 | F | - |
| 8 | F | - |
| 9 | F | - |
| 10 | F | - |
| 11 | F | - |
| 12 | F | - |

![](img/a8f1b433a70f1e5c410c8b43e41b650e_470_0.png)

| v | marked[] | edgeTo[] |
|---|---|---|
| 0 | T | — |
| 1 | F | — |
| 2 | T | 3 |
| 3 | T | 4 |
| 4 | T | 5 |
| 5 | T | 0 |
| 6 | F | — |
| 7 | F | — |
| 8 | F | — |
| 9 | F | — |
| 10 | F | — |
| 11 | F | — |
| 12 | F | — |

done 3
