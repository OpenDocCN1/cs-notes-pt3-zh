| q | move[q].a | move[q].b |
|---|---|---|
| N | -1 | 0 |
| NE | -1 | 1 |
| E | 0 | 1 |
| SE | 1 | 1 |
| S | 1 | 0 |
| SW | 1 | -1 |
| W | 0 | -1 |
| NW | -1 | -1 |

Table of moves

Thus, from [i][j] to [g][h] in SW direction:
g=i+move[SW].a; h=j+move[SW].b;