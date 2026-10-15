# Stage Computation: call

|  | call Dest |  |
|---|---|---|
| Fetch | icode:ifun ← M₁[PC]
valC ← M₄[PC+1]
valP ← PC+5 | Read instruction byte
Read destination address
Compute return point |
| Decode | valB ← R[%esp] | Read stack pointer |
| Execute | valE ← valB + -4 | Decrement stack pointer |
| Memory | M₄[valE] ← valP | Write return value on stack |
| Write back | R[%esp] ← valE | Update stack pointer
Store incremental PC |
| PC update | PC ← valC | Set PC to destination |

+   - Use ALU to decrement stack pointer