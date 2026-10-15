![](bbox=[0.024, 0.059, 0.98, 0.94])

# Pipe control logic

M_icode

E_icode

D_icode

D_bubble

F_stall

| W | icode |  | valE | valM |  | dstE | dstM |  |
|---|---|---|---|---|---|---|---|---|

| M | icode | Cnd |  | valE | valA |  | dstE | dstM |  |
|---|---|---|---|---|---|---|---|---|---|

| E | icode | ifun |  | valC | valA | valB | dstE | dstM | srcA | srcB |
|---|---|---|---|---|---|---|---|---|---|---|---|

| D | icode | ifun |  | rA | rB | valC | valP |  |
|---|---|---|---|---|---|---|---|---|

| F |  |  | predPC |  |  |
|---|---|---|---|---|---|