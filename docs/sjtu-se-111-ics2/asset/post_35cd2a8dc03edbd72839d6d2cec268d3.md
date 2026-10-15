
## A Source

|  |  |  |
|---|---|---|
|  | opl rA, rB |  |
| Decode | valA ← R[rA] | Read operand A |
|  | rmmovl rA, D(rB) |  |
| Decode | valA ← R[rA] | Read operand A |
|  | popl rA |  |
| Decode | valA ← R[%esp] | Read stack pointer |
|  | jxx Dest |  |
| Decode |  | No operand |
|  | call Dest |  |
| Decode |  | No operand |
|  | ret |  |
| Decode | valA ← R[%esp] | Read stack pointer |

```
int srcA = [
    icode in { IRRMOVL, IRMMOVL,
                IOPL, IPUSHl } : rA;
    icode in { IPOPL, IRET } : RESP;
    1 : RNONE; # Don't need register
];
```

## E Destination

|  | Instruction | Write-back | Description |
|---|---|---|---|
|  | opl rA, rB |  |  |
| Write-back | R[rB] ← valE |  | Write back result |
|  | rmmovl rA, D(rB) |  |  |
| Write-back |  | None |  |
|  | popl rA |  |  |
| Write-back | R[%esp] ← valE |  | Update stack pointer |
|  | jxx Dest |  |  |
| Write-back |  | None |  |
|  | call Dest |  |  |
| Write-back | R[%esp] ← valE |  | Update stack pointer |
|  | ret |  |  |
| Write-back | R[%esp] ← valE |  | Update stack pointer |

```
int dstE = [
    icode in { IRRMOVL, IIRMOVL,
                IOPL} : rB;
    icode in { IPUSHL, IPOPL, ICALL,
                IRET } : RESP;
    1 : RNONE;  # Don't need register
];
// not conside cmovXX
```

## Execute Logic

![](img/9bd5f6161cb6607b56d2fb964d1b8794_151_0.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_152_0.png)

- **Predefined Blocks**
  - ALU: implements 4 required functions and generate condition code values
  - CC: register with 3 condition code bits
  - cond: computes condition flag

![](img/9bd5f6161cb6607b56d2fb964d1b8794_153_0.png)

- Control Logical
  - Set CC: Should condition code register be loaded?
  - ALU A: Input A to ALU {valA, valC, +4, -4}
  - ALU B: Input B to ALU {valB, 0}
  - ALU fun: What function should ALU compute?

## ALU A Input

| 阶段 | 指令/ALU 输入 |
|---|---|
| Execute | `OPI rA, rB`<br>`valE ← valB OP valA` |
| Execute | `irmovl rA, D(rB)`<br>`valE ← valB + valC` |
| Execute | `popl rA`<br>`valE ← valB + 4` |
| Execute | `jXX Dest`<br>（空操作） |
| Execute | `call Dest`<br>`valE ← valB + -4` |
| Execute | `ret`<br>`valE ← valB + 4` |

Perform ALU operation

Compute effective address

Increment stack pointer

No operation

Decrement stack pointer

Increment stack pointer

```
int aluA = [
    icode in { IRMMOVL, IOPL } : valA;
    icode in { IIRMOVL, IRMMOVL, IMRMOVL } : valC;
    icode in { ICALL, IPUSHl } : -4;
    icode in { IRET, IPOPL } : 4;
    # Other instructions don't need ALU
];
```

## ALU Operation

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

## ALU Operation / Condition Set

```
int alufun = [
    icode == IOPL : ifun;
    1 : ALUADD;
];
```

```
Bool set_cc = icode in { IOPL };
```

## Memory Logic

- Predefined Blocks
  - Memory: Reads or writes memory word

![](img/9bd5f6161cb6607b56d2fb964d1b8794_159_0.png)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_160_0.png)

- Control Logical
  - Mem. read: should word be read?
  - Mem. write: should word be written?
  - Mem. addr.: Select address {valA, valE}
  - Mem. data.: Select data {valA, valP}

## Memory Address

| Memory | `opl rA, rB` | No operation |
|---|---|---|
| Memory | `mrmovl rA, D(rB)` | Write value to memory |
| Memory | `M₄[valE] ← valA` | Write value to memory |
| Memory | `popl rA` | Read from stack |
| Memory | `valM ← M₄[valA]` | Read from stack |
| Memory | `jxx Dest` | No operation |
| Memory | `call Dest` | Write return value on stack |
| Memory | `M₄[valE] ← valP` | Write return value on stack |
| Memory | `ret` | Read return address |
| Memory | `valM ← M₄[valA]` | Read return address |
