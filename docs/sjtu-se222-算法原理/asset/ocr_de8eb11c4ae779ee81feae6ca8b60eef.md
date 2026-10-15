# Comparison

|  | in-place? | stable? | worst | average | best | remarks |
|---|---|---|---|---|---|---|
| selection | x |  | N² / 2 | N² / 2 | N² / 2 | N exchanges |
| insertion | x | x | N² / 2 | N² / 4 | N | for small N or partially ordered |
| shell | x |  | ? | ? | N | tight code, subquadratic |