# Theoretical foundation:
Functionally complete sets of truth-functional connectives?

Is {¬, ∧, ∨, →, ↔, ⊕} enough ?

| p | q | ¬p | p∧q | p∨q | p⊕q | p→q | p↔q |
|---|---|----|-----|-----|------|------|------|
| T | T | F | T | T | F | T | T |
| T | F | F | F | T | T | F | F |
| F | T | T | F | T | T | T | F |
| F | F | T | F | F | F | T | T |

| p | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| T | F | T | F | T |
| F | F | F | T | T |
|   |   |   | ¬ |   |

Do we need all connectives to represent a complex sentence?

| p | q | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|---|---|---|---|---|---|---|---|---|---|---|---|----|----|----|----|----|----|
| T | T | F | T | F | T | F | T | F | T | F | T | F | T | F | T | F | T |
| T | F | F | F | T | T | F | F | T | T | F | F | T | T | F | F | T | T |
| F | T | F | F | F | F | T | T | T | T | F | F | F | F | T | T | T | T |
| F | F | F | F | F | F | F | F | F | F | T | T | T | T | T | T | T | T |
|   |   |   | ∧ |   |   |   |   |   | ∨ | ↓ | ≡ |    |    |    | ⊃ | ↑ |   |