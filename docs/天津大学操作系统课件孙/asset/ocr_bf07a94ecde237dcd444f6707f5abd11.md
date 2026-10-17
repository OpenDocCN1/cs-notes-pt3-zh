# FIFO

12 references, 9 faults

| Page Refs | Fault? | 3 Page Frames |  |  |
|---|---|---|---|---|
| A | yes | A |  |  |
| B | yes | B | A |  |
| C | yes | C | B | A |
| D | yes | D | C | B |
| A | yes | A | D | C |
| B | yes | B | A | D |
| E | yes | E | B | A |
| A | no | E | B | A |
| B | no | E | B | A |
| C | yes | C | E | B |
| D | yes | D | C | E |
| E | no | D | C | E |