Since the set elements are numbered 0,1,...,n−1, we represent the tree nodes using an array `parent[n]`. The `parent[i]` contains the parent pointer of node i (element i as well).

The root node has a parent of −1.

The following is the array representation of S₁, S₂, and S₃:

|  | [0] | [1] | [2] | [3] | [4] | [5] | [6] | [7] | [8] | [9] |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| parent | -1 | 4 | -1 | 2 | -1 | 2 | 0 | 0 | 0 | 4 |