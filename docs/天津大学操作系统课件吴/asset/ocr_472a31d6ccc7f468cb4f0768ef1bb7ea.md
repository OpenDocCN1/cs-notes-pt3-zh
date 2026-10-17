# # Deadlock Detection with Multiple Resources of Each Type (1)

Resources in existence
(E1, E2, E3, ..., Em)

Resources available
(A1, A2, A3, ..., Am)

Current allocation matrix

Request matrix

| C11 | C12 | C13 | ... | C1m |
|-----|-----|-----|-----|-----|
| C21 | C22 | C23 | ... | C2m |
| ... | ... | ... | ... | ... |
| Cn1 | Cn2 | Cn3 | ... | Cnm |

| R11 | R12 | R13 | ... | R1m |
|-----|-----|-----|-----|-----|
| R21 | R22 | R23 | ... | R2m |
| ... | ... | ... | ... | ... |
| Rn1 | Rn2 | Rn3 | ... | Rnm |

Row n is current allocation
to process n

Row 2 is what process 2 needs

Figure 6-6. The four data structures needed
by the deadlock detection algorithm.