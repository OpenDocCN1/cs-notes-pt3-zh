# # Understanding Pointers & Arrays #2

| Decl | An |  |  | *An |  |  | **An |  |  |
|---|---|---|---|---|---|---|---|---|---|
|  | Cmp | Bad | Size | Cmp | Bad | Size | Cmp | Bad | Size |
| `int A1[3]` | Y | N | 12 | Y | N | 4 | N | — | — |
| `int *A2[3]` | Y | N | 24 | Y | N | 8 | Y | Y | 4 |
| `int (*A3)[3]` | Y | N | 8 | Y | Y | 12 | Y | Y | 4 |
| `int (*A4[3])` | Y | N | 24 | Y | N | 8 | Y | Y | 4 |

![](bbox=[0.025, 0.572, 0.976, 0.97])