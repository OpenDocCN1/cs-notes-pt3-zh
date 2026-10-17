# An example

**Adjacent matrix**

|   |   |   |   |   |
|---|---|---|---|---|
| 1 | 4 | 4 | 8 | 0 |
| 3 | 0 | 1 | 5 | 9 |
| 2 | 2 | 0 | 1 | 8 |
| 8 | 8 | 9 | 0 | 1 |
| 8 | 8 | 2 | 9 | 0 |

**Distance matrix of shortest path**

|   |   |   |   |   |
|---|---|---|---|---|
| 0 | 1 | 2 | 3 | 4 |
| 3 | 0 | 1 | 2 | 3 |
| 2 | 2 | 0 | 1 | 2 |
| 5 | 5 | 5 | 0 | 1 |
| 4 | 4 | 2 | 3 | 0 |

**matrix Rᵢⱼ**

|   |   |   |   |   |
|---|---|---|---|---|
| 0 | 0 | 2 | 3 | 4 |
| 0 | 0 | 0 | 3 | 4 |
| 0 | 0 | 0 | 0 | 4 |
| 5 | 5 | 5 | 0 | 0 |
| 3 | 3 | 0 | 3 | 0 |

+   - we can traceback the shortest paths from matrix $(k_{ij})$, for example, from 1 to 5
+     - $k(1,5)=4$, $k(4,5)=0$, $4 \to 5$ is a sub-path
+     - $k(1,4)=3$, $k(3,4)=0$, $3 \to 4$ is a sub-path