

## Decision-tree model

A decision tree can model the execution of any comparison sort:

- One tree for each input size \(n\).
- View the algorithm as splitting whenever it compares two elements.
- The tree contains the comparisons along all possible instruction traces.
- The running time of the algorithm = the length of the path taken.
- Worst-case running time = height of tree.

## Lower bound for decision-tree sorting

**Theorem.** Any decision tree that can sort \( n \) elements must have height \( \Omega(n \lg n) \).

**Proof.** The tree must contain \( \ge n! \) leaves, since there are \( n! \) possible permutations. A height-\( h \) binary tree has \( \le 2^h \) leaves. Thus, \( n! \le 2^h \).

- \(\therefore \ h \ge \lg(n!)\) (lg is mono. increasing)
- \(\ge \lg \left((n/e)^n\right)\) (Stirling's formula)
- \(= n \lg n - n \lg e\)
- \(= \Omega(n \lg n)\).

## Lower bound for comparison sorting

**Corollary.** Heapsort and merge sort are asymptotically optimal comparison sorting algorithms.

## Sorting in linear time

**Counting sort:** No comparisons between elements.

- **Input**: \( A[1 \dots n] \), where \( A[j] \in \{1, 2, \dots, k\} \).
- **Output**: \( B[1 \dots n] \), sorted.
- **Auxiliary storage**: \( C[1 \dots k] \).

## Counting sort

```
for i ← 1 to k
do C[i] ← 0
for j ← 1 to n
do C[A[j]] ← C[A[j]] + 1  ▷ C[i] = |{key = i}|
for i ← 2 to k
do C[i] ← C[i] + C[i−1]  ▷ C[i] = |{key ≤ i}|
for j ← n downto 1
do B[C[A[j]]] ← A[j]
   C[A[j]] ← C[A[j]] − 1
```

## Counting-sort example

```
A: [4, 1, 3, 4, 3]
```

```
C: [_, _, _, _]
```

```
B: [_, _, _, _, _]
```

## Loop 1

for \( i \leftarrow 1 \text{ to } k \)
do \( C[i] \leftarrow 0 \)

![](img/5e59105b951890406cf98b2a964cb2f9_342_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_342_1.png)

![](img/5e59105b951890406cf98b2a964cb2f9_342_2.png)

## Loop 2

A: 4 1 3 4 3

C: 0 0 0 1

B:

for \( j \leftarrow 1 \text{ to } n \)
do \( C[A[j]] \leftarrow C[A[j]] + 1 \quad \triangleright C[i] = |\{\text{key} = i\}| \)

## Loop 2

A: 4 1 3 4 3

C: 1 0 0 1

B:

for \( j \leftarrow 1 \text{ to } n \)

do \( C[A[j]] \leftarrow C[A[j]] + 1 \quad \triangleright C[i] = |\{\text{key} = i\}| \)

## Loop 2

for \( j \leftarrow 1 \text{ to } n \)
do \( C[A[j]] \leftarrow C[A[j]] + 1 \quad \triangleright C[i] = |\{\text{key} = i\}| \)

![](img/5e59105b951890406cf98b2a964cb2f9_345_0.png)

![](img/5e59105b951890406cf98b2a964cb2f9_345_1.png)

![](img/5e59105b951890406cf98b2a964cb2f9_345_2.png)

## Loop 2

1   2   3   4   5

A: 4   1   3   4   3

1   2   3   4

C: 1   0   1   2

B:

for \( j \leftarrow 1 \text{ to } n \)
do \( C[A[j]] \leftarrow C[A[j]] + 1 \quad \triangleright C[i] = |\{ \text{key} = i \}| \)

## Loop 2

A: 4 1 3 4 3
C: 1 0 2 2
B:

```
for j ← 1 to n
do C[A[j]] ← C[A[j]] + 1 ▷ C[i] = |{key = i}|
```

## Loop 3

A: 4 1 3 4 3

C: 1 0 2 2

B:

C': 1 1 2 2

for \( i \leftarrow 2 \text{ to } k \)
do \( C[i] \leftarrow C[i] + C[i-1] \)  \(\triangleright C[i] = |\{\text{key} \le i\}|\)

## Loop 3

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| 4 | 1 | 3 | 4 | 3 |

C: | 1 | 2 | 3 | 4 |
|---|---|---|---|
| 1 | 0 | 2 | 2 |

B: | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
|   |   |   |   |   |

C′: | 1 | 2 | 3 | 4 |
|---|---|---|---|
| 1 | 1 | 3 | 2 |

for *i* ← 2 to *k*

do C[*i*] ← C[*i*] + C[*i*−1]

▷ C[*i*] = |{key ≤ *i*}|

## Loop 3

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|
| 4 | 1 | 3 | 4 | 3 |

A:

| 1 | 2 | 3 | 4 |
|---|---|---|---|
| 1 | 0 | 2 | 2 |

C:

|  |  |  |  |
|---|---|---|---|
|  |  |  |  |

B:

| 1 | 1 | 3 | 5 |
|---|---|---|---|
| 1 | 1 | 3 | 5 |

C′:

```
for i ← 2 to k
    do C[i] ← C[i] + C[i−1]
```

▷ C[i] = |{key ≤ i}|

## Loop 4

![](img/5e59105b951890406cf98b2a964cb2f9_352_0.png)

```
for $j \leftarrow n$ downto 1
    do $B[C[A[j]]] \leftarrow A[j]$
       $C[A[j]] \leftarrow C[A[j]] - 1$
```

