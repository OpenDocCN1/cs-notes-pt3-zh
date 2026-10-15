
## Dijkstra 3-way partitioning
- Let v be partitioning item a[lo].
- Scan i from left to right.
  - (a[i] < v): exchange a[lt] with a[i] and increment both lt and i
  - (a[i] > v): exchange a[gt] with a[i] and decrement gt
  - (a[i] == v): increment i

![](img/a8f1b433a70f1e5c410c8b43e41b650e_180_0.png)

invariant

![](img/a8f1b433a70f1e5c410c8b43e41b650e_180_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_181_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_181_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_182_0.png)

invariant

![](img/a8f1b433a70f1e5c410c8b43e41b650e_182_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_183_0.png)

invariant

![](img/a8f1b433a70f1e5c410c8b43e41b650e_183_1.png)

- Let `v` be partitioning item `a[lo]`.
- Scan `i` from left to right.
  - `(a[i] < v):` exchange `a[lt]` with `a[i]` and increment both `lt` and `i`
  - `(a[i] > v):` exchange `a[gt]` with `a[i]` and decrement `gt`
  - `(a[i] == v):` increment `i`

![](img/a8f1b433a70f1e5c410c8b43e41b650e_185_0.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_185_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_186_0.png)

invariant

![](img/a8f1b433a70f1e5c410c8b43e41b650e_186_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_187_0.png)

invariant

![](img/a8f1b433a70f1e5c410c8b43e41b650e_187_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_188_0.png)

invariant

![](img/a8f1b433a70f1e5c410c8b43e41b650e_188_1.png)

![](img/a8f1b433a70f1e5c410c8b43e41b650e_189_0.png)

invariant

![](img/a8f1b433a70f1e5c410c8b43e41b650e_189_1.png)

## Bentley-McIlroy 3-Way Partitioning

![](img/a8f1b433a70f1e5c410c8b43e41b650e_190_0.png)

## Bentley-McIlroy 3-way partitioning

Repeat until i and j pointers cross.

- Scan i from left to right so long as a[i] < a[lo].
- Scan j from right to left so long as a[j] > a[lo].
- Exchange a[i] with a[j].
- If a[i] == a[lo], exchange a[i] with a[p] and increment p.
- If a[j] == a[lo], exchange a[j] with a[q] and decrement q.

![](img/a8f1b433a70f1e5c410c8b43e41b650e_192_0.png)
