

## Dynamic-programming hallmark #1

### Optimal substructure

An optimal solution to a problem (instance) contains optimal solutions to subproblems.

If z = LCS(x, y), then any prefix of z is an LCS of a prefix of x and a prefix of y.

## Recursive algorithm for LCS

```
$$\begin{aligned}
\mathrm{LCS}(x,y,i,j)\\
\quad\textbf{if }x[i]=y[j]\\
\qquad\textbf{then }c[i,j]\leftarrow \mathrm{LCS}(x,y,i-1,j-1)+1\\
\qquad\textbf{else }c[i,j]\leftarrow \max\{\mathrm{LCS}(x,y,i-1,j),\\
\hspace{6.7em}\mathrm{LCS}(x,y,i,j-1)\}
\end{aligned}$$
```

## Recursive algorithm for LCS

LCS(x, y, i, j)
if x[i] = y[j]
then c[i, j] ← LCS(x, y, i−1, j−1) + 1
else c[i, j] ← max { LCS(x, y, i−1, j),
LCS(x, y, i, j−1)}

**Worst-case:** x[i] ≠ y[j], in which case the algorithm evaluates two subproblems, each with only one parameter decremented.

## Recursion tree

m = 3, n = 4:

![](img/5e59105b951890406cf98b2a964cb2f9_547_0.png)

m = 3, n = 4:

![](img/5e59105b951890406cf98b2a964cb2f9_548_0.png)

Height = m + n ⇒ work potentially exponential.

m = 3, n = 4:

![](img/5e59105b951890406cf98b2a964cb2f9_549_0.png)

same subproblem

m + n

Height = m + n ⇒ work potentially exponential, but we’re solving subproblems already solved!

## Dynamic-programming hallmark #2

### Overlapping subproblems

A recursive solution contains a “small” number of distinct subproblems repeated many times.

![](img/5e59105b951890406cf98b2a964cb2f9_550_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_551_0.png)

### Dynamic-programming hallmark #2

> **Overlapping subproblems**
> 
> A recursive solution contains a “small” number of distinct subproblems repeated many times.

The number of distinct LCS subproblems for two strings of lengths m and n is only mn.

![](img/5e59105b951890406cf98b2a964cb2f9_552_0.png)

### Memoization algorithm

Memoization: After computing a solution to a subproblem, store it in a table. Subsequent calls check the table to avoid redoing work.

```
LCS(x, y, i, j)
if c[i, j] = NIL
    then if x[i] = y[j]
        then c[i, j] ← LCS(x, y, i−1, j−1) + 1
        else c[i, j] ← max { LCS(x, y, i−1, j),
                             LCS(x, y, i, j−1) }
```

![](img/5e59105b951890406cf98b2a964cb2f9_554_0.png)

### Memoization algorithm

Memoization: After computing a solution to a subproblem, store it in a table. Subsequent calls check the table to avoid redoing work.

```
LCS(x, y, i, j)

if c[i,j] = NIL
then if x[i] = y[j]
then c[i,j] ← LCS(x, y, i-1, j-1) + 1
else c[i,j] ← max { LCS(x, y, i-1, j),
LCS(x, y, i, j-1)}
```

Time = Θ(mn) = constant work per table entry.

Space = Θ(mn).

same as before

## Dynamic-programming algorithm

### IDEA:

Compute the table bottom-up.

![](img/5e59105b951890406cf98b2a964cb2f9_555_0.png)

## Dynamic-programming algorithm

### IDEA:

Compute the table bottom-up.
Time = $\Theta(mn)$.

|   | A | B | C | B | D | A | B |
|---|---|---|---|---|---|---|---|
|   | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| B | 0 | 0 | 1 | 1 | 1 | 1 | 1 |
| D | 0 | 0 | 1 | 1 | 1 | 2 | 2 |
| C | 0 | 0 | 1 | 2 | 2 | 2 | 2 |
| A | 0 | 1 | 1 | 2 | 2 | 2 | 3 |
| B | 0 | 1 | 2 | 2 | 3 | 3 | 3 |
| A | 0 | 1 | 2 | 2 | 3 | 3 | 4 |

## Dynamic-programming algorithm

### IDEA:

Compute the table bottom-up.
Time = Θ(mn).
Reconstruct LCS by tracing backwards.

|   | A   | B   | C   | B   | D   | A   | B   |
|---|-----|-----|-----|-----|-----|-----|-----|
|   | 0   | 0   | 0   | 0 | 0   | 0   | 0   |
| B | 0   | 0   | 1   | 1   | 1   | 1   | 1   |
| D | 0   | 0   | 1   | 1   | 2   | 2   | 2   |
| C | 0   | 0   | 1   | 2   | 2   | 2   | 2   |
| A | 0   | 1   | 1   | 2   | 2   | 3   | 3   |
| B | 0   | 1   | 2   | 3   | 3   | 3   | 4   |
| A | 0   | 1   | 2   | 3   | 3   | 4   | 4   |

