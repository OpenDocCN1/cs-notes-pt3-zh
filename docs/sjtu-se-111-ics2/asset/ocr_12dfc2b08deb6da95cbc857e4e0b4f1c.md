# ALU Operation

| Stage | Instruction / Operation |
|---|---|
|  | `opl rA, rB` |
| Execute | `valE ← valB OP valA` |
|  | `rrmovl rA, D(rB)` |
| Execute | `valE ← valB + valC` |
|  | `popl rA` |
| Execute | `valE ← valB + 4` |
|  | `jXX Dest` |
| Execute |  |
|  | `call Dest` |
| Execute | `valE ← valB + -4` |
|  | `ret` |
| Execute | `valE ← valB + 4` |

Perform ALU operation

Compute effective address

Increment stack pointer

No operation

Decrement stack pointer

Increment stack pointer