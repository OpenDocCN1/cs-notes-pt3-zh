
## Software/hardware interface

## Compiler allocates data structures to memory

## Compiler associating variables with registers

## Actual MIPS memory addresses and contents

![](img/273e5640629250d9497f523c984c99c0_70_0.png)

### The offset to be added to $s3 in Example 2.4 must be 4×8

### Example 2.5 Compiling using **load and store**

C code:

```
A[12] = h + A[8];  // A is an array of 100 words
(Assume: h ---- $s2   base address of A ---- $s3)
```

MIPS code:

```
lw    $t0, 32($s3)     # temporary reg $t0 gets A[8]
add   $t0, $s2, $t0     # temporary reg $t0 gets h + A[8]
sw    $t0, 48($s3)      # stores h + A[8] back into A[12]
```

### Example 2.6 Compiling using a variable array index

C code:

```
g = h + A[i]; // A is an array of 100 words
(Assume: g, h, i---- $s1, $s2, $s4 base address of A ---- $s3)
```

MIPS code:

```
add $t1, $s4, $s4 # temp reg $t1 = 2 * i
add $t1, $t1, $t1 # temp reg $t1 = 4 * i
add $t1, $t1, $s3 # $t1 = address of A[i] (4 * i + $s3)
lw $t0, 0($t1) # temp reg $t0 = A[i]
add $s1, $s2, $t0 # g = h + A[i]
```

### Spilling registers:

Putting less commonly used variables (or those needed later) into memory.

## 2.4 Representing Instructions in the Computer --- Instruction Format

- All information in computer consists of binary bits
- Mapping registers into numbers
  - Map registers $s0 to $s7 onto registers 16 to 23
  - Map registers $t0 to $t7 onto registers 8 to 15
- Example 2.7 Translating assembly into machine instruction
  - MIPS code

    ```
    add $t0, $s1, $s2
    ```

  - Decimal version of machine code

    ```
    | 0 | 17 | 18 | 8 | 0 | 32 |
    ```

  - Binary version of machine code

    ```
    | 000000 | 10001 | 10010 | 01000 | 00000 | 100000 |
    6 bits 5 bits 5 bits 5 bits 5 bits 6 bits
    ```

### MIPS fields (format)

**R-type or R-format**

| op | rs | rt | rd | shamt | funct |
|---|---|---|---|---|---|
| 6 bits | 5 bits | 5 bits | 5 bits | 5 bits | 6 bits |

**I-type or I-format**

| op | rs | rt | address |
|---|---|---|---|
| 6 bits | 5 bits | 5 bits | 16 bits |

### Must bear in mind!

- op: basic operation of the instruction, traditionally called the opcode.
- rs: the first register source operand.
- rt: the second register source operand.
- rd: the register destination operand.
- shamt: shift amount.
- funct: function, this field selects the specific variant of the operation in the op field.

![](img/273e5640629250d9497f523c984c99c0_76_0.png)

### Design Principle 3

Good design demands good compromises

### All instructions in MIPS have the same length

Conflict: same length <----> single instruction

### Example 2.8 Translating assembly into machine instruction

C code:

```
A[300] = h + A[300];
(Assume: h ---- $s2 base address of A ---- $t1)
```

MIPS assembly code:

```
lw $t0, 1200($t1) # temporary reg $t0 gets A[300]
add $t0, $s2, $t0 # temporary reg $t0 gets h + A[300]
sw $t0, 1200($t1) # stores h + A[300] back into A[300]
```

### MIPS machine language code:

### Decimal version

| instruction | op | rs | rt | rd | address/shamt | funct |
|---|---|---|---|---|---|---|
| lw | 35 | 9 | 8 |  | 1200 |  |
| add | 0 | 18 | 8 | 8 | 0 | 32 |
| sw | 43 | 9 | 8 |  | 1200 |  |

### Binary version

| instruction | op | rs | rt | rd | address/shamt | funct |
|---|---|---|---|---|---|---|
| lw | 100011 | 01001 | 01000 |  | 0000 0100 1011 0000 |  |
| add | 000000 | 10010 | 01000 | 01000 | 00000 | 100000 |
| sw | 101011 | 01001 | 01000 |  | 0000 0100 1011 0000 |  |

### Note the only difference of the first and last instructions!

### Two key principles of today’s computers

- Instructions are represented as numbers
- Programs can be stored in memory like numbers

![](img/273e5640629250d9497f523c984c99c0_79_0.png)

### Stored-program concept

![](img/273e5640629250d9497f523c984c99c0_80_0.png)

2.4 Instruction Format
