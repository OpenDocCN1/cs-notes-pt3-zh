
## Kosaraju-Sharir

**Phase 1.** Compute reverse postorder in $G^R$.

3  11  9  12  10  6  7  8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_513_0.png)

| v | marked[v] |
|---|---|
| 0 | T |
| 1 | F |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

visit 5

## Phase 1. Compute reverse postorder in $G^R$.

5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_514_0.png)

5 done

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | F |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

## Phase 1. Compute reverse postorder in $G^R$.

4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_515_0.png)

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | F |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

4 done

## Phase 1. Compute reverse postorder in $G^R$.

4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_516_0.png)

visit 2

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | F |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

## Phase 1. Compute reverse postorder in $G^R$.

2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_517_0.png)

2 done

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | F |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

## Phase 1. Compute reverse postorder in $G^R$.

0 2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_518_0.png)

0 done

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | F |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

## Phase 1. Compute reverse postorder in $G^R$.

0 2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_519_0.png)

visit 1

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | T |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

## Phase 1. Compute reverse postorder in $G^R$.

1 0 2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_520_0.png)

1 done

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | T |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

## Phase 1. Compute reverse postorder in $G^R$.

1 0 2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_521_0.png)

| v | marked[v] |
|---|-----------|
| 0 | T |
| 1 | T |
| 2 | T |
| 3 | T |
| 4 | T |
| 5 | T |
| 6 | T |
| 7 | T |
| 8 | T |
| 9 | T |
| 10 | T |
| 11 | T |
| 12 | T |

check 2 3 4 5 6 7 8 9 10 11 12

## Kosaraju-Sharir

**Phase 1.** Compute reverse postorder in $G^R$.

1  0  2  4  5  3  11  9  12  10  6  7  8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_522_0.png)

reverse digraph $G^R$

- DFS in reverse graph
- DFS in original graph

## Phase 2. Run DFS in G, visiting unmarked vertices in reverse postorder of G^R.

1 0 2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_524_0.png)

original digraph G

| v | scc[v] |
|---|--------|
| 0 | - |
| 1 | - |
| 2 | - |
| 3 | - |
| 4 | - |
| 5 | - |
| 6 | - |
| 7 | - |
| 8 | - |
| 9 | - |
| 10 | - |
| 11 | - |
| 12 | - |

## Phase 2. Run DFS in G, visiting unmarked vertices in reverse postorder of G^R.

1 0 2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_525_0.png)

| v | scc[v] |
|---|--------|
| 0 | _ |
| 1 | 0 |
| 2 | _ |
| 3 | _ |
| 4 | _ |
| 5 | _ |
| 6 | _ |
| 7 | _ |
| 8 | _ |
| 9 | _ |
| 10 | _ |
| 11 | _ |
| 12 | _ |

visit 1

## Phase 2. Run DFS in G, visiting unmarked vertices in reverse postorder of G^R.

1 0 2 4 5 3 11 9 12 10 6 7 8

![](img/a8f1b433a70f1e5c410c8b43e41b650e_526_0.png)

| v | scc[v] |
|---|--------|
| 0 | - |
| 1 | 0 |
| 2 | - |
| 3 | - |
| 4 | - |
| 5 | - |
| 6 | - |
| 7 | - |
| 8 | - |
| 9 | - |
| 10 | - |
| 11 | - |
| 12 | - |

1 done
