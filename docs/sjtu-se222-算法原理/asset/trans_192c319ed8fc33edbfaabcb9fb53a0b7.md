

## 练习

- 从我们的课程主页下载 hw7.pdf
- 截止日期为 10 月 28 日

## 挑战

### Challenge 1

**Problem.** Is a graph bipartite?

### How difficult?

- Any programmer could do it.
- Need to be a typical diligent SE222 student.
- Hire an expert.
- Intractable.
- No one knows.
- Impossible.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_420_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_420_1.png)

### Challenge 1

**Problem.** Is a graph bipartite?

### How difficult?

- Any programmer could do it.
- Need to be a typical diligent SE222 student.
- Hire an expert.
- Intractable.
- No one knows.
- Impossible.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_421_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_421_1.png)

### Challenge 3

**Problem.** Find a cycle that uses every edge exactly once. (Eulerian tour)

### How difficult?

- Any programmer could do it.
- Need to be a typical diligent SE222 student.
- Hire an expert.
- Intractable.
- No one knows.
- Impossible.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_423_0.png)

0-1-2-3-4-2-0-6-4-5-0

![](img/a8f1b433a70f1e5c410c8b43e41b650e_423_1.png)

### Challenge 4

**Problem.** Find a cycle that uses every vertex exactly once. (Hamiltonian tour)

### How difficult?

- Any programmer could do it.
- Need to be a typical diligent SE222 student.
- Hire an expert.
- Intractable. ✓
- No one knows.
- Impossible.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_424_0.png)

### Challenge 5

**Problem.** Are two graphs identical except for vertex names? (Graph isomorphism)

### How difficult?

- Any programmer could do it.
- Need to be a typical diligent SE222 student.
- Hire an expert.
- Intractable.
- No one knows. ✓
- Impossible.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_425_0.png)

```
0-1
0-2
0-5
0-6
3-4
3-5
4-5
4-6
```

![](img/a8f1b433a70f1e5c410c8b43e41b650e_425_1.png)

```
0-4
0-5
0-6
1-4
1-5
2-4
3-4
5-6
```

0 → 4, 1 → 3, 2 → 2, 3 → 6, 4 → 5, 5 → 0, 6 → 1

### Challenge 6

**Problem.** Lay out a graph in the plane without crossing edges?

### How difficult?

- Any programmer could do it.
- Need to be a typical diligent SE222 student.
- Hire an expert. ✓
- Intractable.
- No one knows.
- Impossible.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_426_0.png)

```
0-1
0-2
0-5
0-6
3-4
3-5
4-5
4-6
```

![](img/a8f1b433a70f1e5c410c8b43e41b650e_426_1.png)

## 4.1 Breadth-First Search

![](img/a8f1b433a70f1e5c410c8b43e41b650e_427_0.png)

click to begin demo

### Breadth-first search

Repeat until queue is empty:

- Remove vertex v from queue.
- Add to queue all unmarked vertices adjacent to v and mark them.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_428_0.png)

graph G

```
tinyDG.txt
V 6
E 8
0 5
2 4
2 3
1 2
0 1
3 4
3 5
0 2
```

### Breadth-first search

Repeat until queue is empty:

- Remove vertex v from queue.
- Add to queue all unmarked vertices adjacent to v and mark them.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_429_0.png)

queue

| v | edgeTo[v] |
|---|---|
| 0 | - |
| 1 | - |
| 2 | - |
| 3 | - |
| 4 | - |
| 5 | - |

add 0 to queue

### Breadth-first search

Repeat until queue is empty:

- Remove vertex *v* from queue.
- Add to queue all unmarked vertices adjacent to *v* and mark them.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_430_0.png)

dequeue 0

### Breadth-first search

Repeat until queue is empty:

- Remove vertex $v$ from queue.
- Add to queue all unmarked vertices adjacent to $v$ and mark them.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_431_0.png)

queue

| v | edgeTo[v] |
|---|---|
| 0 | — |
| 1 | — |
|   | 0 |
| 2 | — |
| 3 | — |
| 4 | — |
| 5 | — |

dequeue 0

### Breadth-first search

Repeat until queue is empty:

- Remove vertex v from queue.
- Add to queue all unmarked vertices adjacent to v and mark them.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_432_0.png)

queue

| v | edgeTo[v] |
|---|---|
| 0 | — |
| 1 | 0 |
| 2 | 0 |
| 3 | — |
| 4 | — |
| 5 | — |

dequeue 0

