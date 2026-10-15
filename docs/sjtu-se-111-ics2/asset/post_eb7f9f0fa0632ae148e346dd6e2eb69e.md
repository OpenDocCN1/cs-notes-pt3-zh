
## Executing pushl

```
`pushl rA`  `a 0 rA F`
```

- **Fetch**
  - Read 2 bytes
- **Decode**
  - Read stack pointer and register rA
- **Execute**
  - Decrement stack pointer by 4

- **Memory**
  - Store valA at the address of new stack pointer
- **Write back**
  - Update stack pointer
- **PC Update**
  - Increment PC by 2

## Stage Computation: pushl

|  | pushl rA |  |
|---|---|---|
| Fetch | icode:ifun ← M₁[PC]
rA:rB ← M₁[PC+1]
valP ← PC+2 | Read instruction byte
Read register byte
Compute next PC |
| Decode | valA ← R[rA]
valB ← R[%esp] | Read valA
Read stack pointer |
| Execute | valE ← valB + (-4) | Decrement stack pointer |
| Memory | M₄[valE] ← valA | Store to stack |
| Write back | R[%esp] ← valE | Update stack pointer |
| PC update | PC ← valP | Update PC |

- Use ALU to decrement stack pointer

## Executing popl

```
popl rA
b 0 rA F
```

- Fetch
  - Read 2 bytes
- Decode
  - Read stack pointer
- Execute
  - Increment stack pointer by 4

- Memory
  - Read from old stack pointer
- Write back
  - Update stack pointer
  - Update register rA
- PC Update
  - Increment PC by 2

## Stage Computation: popl

|  | popl rA |  |
|---|---|---|
| Fetch | icode:ifun ← M₁[PC]
rA:rB ← M₁[PC+1]
valP ← PC+2 | Read instruction byte
Read register byte
Compute next PC |
| Decode | valA ← R[%esp]
valB ← R[%esp] | Read stack pointer
Read stack pointer |
| Execute | valE ← valB + 4 | Increment stack pointer |
| Memory | valM ← M₄[valA] | Read from stack |
| Write back | R[%esp] ← valE
R[rA] ← valM | Update stack pointer
Write back result |
| PC update | PC ← valP | Update PC |

- Use ALU to increment stack pointer

update two registers (special: rA=%esp)

## Executing Jumps

![](img/9bd5f6161cb6607b56d2fb964d1b8794_104_0.png)

## Stage Computation: Jumps

|  | jXX Dest |
|---|---|
| Fetch | icode:ifun ← M₁[PC]
valC ← M₄[PC+1]
valP ← PC+5 |
| Decode |  |
| Execute | Cnd ← Cond(CC,ifun) |
| Memory |  |
| Write back |  |
| PC update | PC ← Cnd ? valC : valP |

Read instruction byte

Read destination address
Fall through address

Compute both addresses

Take branch?

Update PC

Chose based on CC and ifun

![](img/9bd5f6161cb6607b56d2fb964d1b8794_107_0.png)

## Executing call

- Fetch
  - Read 5 bytes
  - Increment PC by 5
- Decode
  - Read stack pointer
- Execute
  - Decrement stack pointer by 4
- Memory
  - Write incremented PC to new value of stack pointer
- Write back
  - Update stack pointer
- PC Update
  - Set PC to Dest

## Stage Computation: call

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

- Use ALU to decrement stack pointer

![](img/9bd5f6161cb6607b56d2fb964d1b8794_111_0.png)

## Executing ret

- Fetch
  - Read 1 byte
- Decode
  - Read stack pointer
- Execute
  - Increment stack pointer by 4
- Memory
  - Read return address from old stack pointer
- Write back
  - Update stack pointer
- PC Update
  - Set PC to return address

## Stage Computation: ret

|  | ret |  |
|---|---|---|
| Fetch | icode:ifun ← M₁[PC] | Read instruction byte |
| Decode | valA ← R[%esp]
valB ← R[%esp] | Read operand stack
Reinterpret operand stack pointer |
| Execute | valE ← valB + 4 | increment stack pointer |
| Memory | valM ← M₄[valA] | Read return address |
| Write back | R[%esp] ← valE | Update stack pointer |
| PC update | PC ← valM | Set PC to return address |

- Use ALU to increment stack pointer
