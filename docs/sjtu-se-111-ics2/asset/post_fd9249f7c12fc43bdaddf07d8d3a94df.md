
![](img/9bd5f6161cb6607b56d2fb964d1b8794_128_0.png)

## SEQ CPU Implementation

## Outline

- SEQ Implementation
- Suggested Reading 4.3.2, 4.3.4

## What we will discuss today?

- The implementation of a sequential CPU (SEQ)
  - Every instruction is finished in one cycle.
  - Instructions execute sequentially.
  - No two instructions execute in parallel or overlap.

## SEQ Hardware Structure

- Stages
  - **Fetch**: Read instruction from memory
  - **Decode**: Read program registers
  - **Execute**: Compute value or address
  - **Memory**: Read or write data
  - **Write Back**: Write program registers
  - **PC**: Update program counter

PC

Write Back

Memory

Execute

Decode

Fetch

![](img/9bd5f6161cb6607b56d2fb964d1b8794_133_0.png)

valM

Data memory

addrs, data

a

valE

CC

ALU

aluA, aluB

valA, valB

srcA, srcB

dstE, dstM

A B F  
Register File

valE, valM

icode:ifun,  
rA:rB

Instruction memory

PC increment

PC

newPC

## Difference between semantics and implementation

- ISA
  - Every stage may update some state; these updates occur sequentially.
- SEQ
  - All state update operations occur simultaneously at the clock rising edge.

![](img/9bd5f6161cb6607b56d2fb964d1b8794_135_0.png)

## SEQ Hardware

- Blue boxes: □ redesigned hardware blocks
  - e.g., memories, ALU
- Gray boxes: ▭ control logic
  - Described in HCL
- White ovals: ○ labels for signals
- Thick lines: → 32-bit word values
- Thin lines: → 4–8-bit values
- Dotted lines: .......→ 1-bit values

## Fetch Logic

![](img/9bd5f6161cb6607b56d2fb964d1b8794_137_0.png)

## Fetch Logic

- Predefined Blocks
  - PC: Register containing PC
  - Instruction memory: Read 6 bytes (PC to PC+5)
  - Split: Divide instruction byte into icode and ifun
  - Align: Get fields for rA, rB, and valC

![](img/9bd5f6161cb6607b56d2fb964d1b8794_138_0.png)

## Fetch Logic

![](img/9bd5f6161cb6607b56d2fb964d1b8794_139_0.png)

- **Control Blocks**
  - **Instr. Valid:** Is this instruction valid?
  - **Need regids:** Does this instruction have a register byte?
  - **Need valC:** Does this instruction have a constant word?
  - **icode|ifun:** Set to “nop” if `imem_error`

## Some Macros

| Name | Value | Meaning |
|---|---|---|
| RESP | 6 | Register ID for `%esp` |
| RNONE | F | Indicates no register file access |
| ALUADD | 0 | Function for addition operation |
| SAOK | 1 | Status code for normal operations |
| SADR | 2 | Status code for address exception |
| SINS | 3 | Status code for illegal instruction exception |
| SHLT | 4 | Status code for `halt` |

| Instruction | Byte Encoding | Operands |
|---|---|---|
| `nop` | `0 0` | |
| `halt` | `1 0` | |
| `rrmovl rA, rB` | `2 0` | `rA rB` |
| `irmovl V, rB` | `3 0 8 rB V` | |
| `rmmovl rA, D(rB)` | `4 0 rA rB D` | |
| `mrmovl D(rB), rA` | `5 0 rA rB D` | |
| `OP1 rA, rB` | `6 fn rA rB` | |
| `jXX Dest` | `7 fn Dest` | |
| `call Dest` | `8 0 Dest` | |
| `ret` | `9 0` | |
| `pushl rA` | `A 0 rA 8` | |
| `popl rA` | `B 0 rA 8` | |

`need_regids`

## Fetch Control Logic

```c
bool need_regids = icode in
{ IRRMOVL, IIRMOVL, IRMMOVL,
IMRMOVL, IOPL, IPUSHL, IPOPL };

bool instr_valid = icode in
{ INOP, IHALT, IRRMOVL, IIRMOVL,
IRMMOVL, IMRMOVL, IOPL, IJXX,
ICALL, IRET, IPUSHL, IPOPL };
```

## Decode & Write-Back Logic

![](img/9bd5f6161cb6607b56d2fb964d1b8794_144_0.png)

## Decode & Write-Back Logic

![](img/9bd5f6161cb6607b56d2fb964d1b8794_145_0.png)

- Predefined Blocks
  - Register File
    - Read ports A, B & write ports E, M
    - Addresses are register IDs or F (no access)

## Decode & Write-Back Logic

- Control Logic
  - srcA: read port address for valA `{rA, %esp}`
  - srcB: read port address for valB `{rB, %esp}`
  - dstE: write port address for valE `{rB, %esp}`
  - dstM: write port address for valM `{rA}`
  - Cnd: used to decide whether to set valE (cmovXX)

![](img/9bd5f6161cb6607b56d2fb964d1b8794_146_0.png)
