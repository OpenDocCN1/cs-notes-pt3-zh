# # Another Division Example

Relations r, s:

| A | B | C | D | E |
|---|---|---|---|---|
| α | a | α | a | 1 |
| α | b | γ | a | 1 |
| α | b | γ | b | 1 |
| β | a | γ | a | 1 |
| γ | a | γ | c | 2 |
| β | a | γ | b | 3 |
| γ | a | γ | a | 1 |
| γ | a | γ | b | 1 |
| γ | c | β | b | 1 |

| D | E |
|---|---|
| a | 1 |
| b | 1 |

| A | B | C |
|---|---|---|
| α | b | γ |
| γ | a | γ |

| A | B | C | D | E |
|---|---|---|---|---|
| α | a | α | a | 1 |
| α | b | γ | a | 1 |
| α | b | γ | b | 1 |
| β | a | γ | a | 1 |
| β | a | γ | b | 3 |
| γ | a | γ | c | 2 |
| γ | a | γ | a | 1 |
| γ | a | γ | b | 1 |
| γ | c | β | b | 1 |

To group all tuples in ‘r ’ on the values of (A,B,C). For each group, if the set under D, E covers ‘s’, then the group value should be added to the answer.

Database System Concepts

2.47