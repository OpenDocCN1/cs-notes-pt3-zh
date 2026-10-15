To identify test cases with decision tables, we interpret conditions as inputs and actions as outputs.

# Decision Table for Triangle Problem

| Conditions / Actions | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| c1: a,b,c form a triangle? | N | Y | Y | Y | Y | Y | Y | Y |
| c2: a=b? | — | Y | Y | Y | Y | N | N | N |
| c3: a=c? | — | Y | Y | N | N | Y | Y | N |
| c4: b=c? | — | Y | N | Y | N | Y | N | Y |
| a1: Not a triangle | X |  |  |  |  |  |  |  |
| a2: Scalene |  |  |  |  |  |  |  | X |
| a3: Isosceles |  |  |  | X |  | X | X |  |
| a4: Equilateral |  | X |  |  |  |  |  |  |
| a5: Impossible |  |  | X | X |  | X |  |  |