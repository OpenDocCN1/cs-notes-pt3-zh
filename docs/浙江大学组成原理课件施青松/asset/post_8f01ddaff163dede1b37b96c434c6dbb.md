
## MIPS operands, assembly and machine language

| Name | Example | Comments |
|---|---|---|
| **32 registers** | `$s0, $s1, …, $s7`<br>`$t0, $t1, …, $t7` | Fast locations for data. In MIPS, data must be in registers to perform arithmetic. Registers `$s0-$s7` map to 16-23 and `$t0-$t7` map to 8-15. |
| **2³⁰ memory words** | `Memory[0]`, `Memory[4]`, …, `Memory[4294967292]` | Accessed only by data transfer instructions in MIPS. MIPS uses byte addresses, so sequential word addresses differ by 4. Memory holds data structures, arrays, and spilled registers. |

| Category | Instruction | Example | Meaning | Comments |
|---|---|---|---|---|
| **Arithmetic** | add | `add $s1, $s2, $s3` | `$s1 = $s2 + $s3` | Three register operands |
| | subtract | `sub $s1, $s2, $s3` | `$s1 = $s2 - $s3` | Three register operands |
| | Add immediate | `addi $s1, $s2, 100` | `$s1 = $s2 + 100` | Used to add constants |
| **Data transfer** | load word | `lw $s1, 100($s2)` | `$s1 = Memory[$s2 + 100]` | Data from memory to register |
| | store word | `sw $s1, 100($s2)` | `Memory[$s2 + 100] = $s1` | Data from register to memory |

| Name | Format | Example | Comment |
|---|---|---|---|
| add | R | `0 18 19 17 0 32` | `add $s1, $s2, $s3` |
| sub | R | `0 18 19 17 0 34` | `sub $s1, $s2, $s3` |
| addi | I | `8 18 17 100` | `addi $s1, $s2, 100` |
| lw | I | `35 18 17 100` | `lw $s1, 100($s2)` |
| sw | I | `43 18 17 100` | `sw $s1, 100($s2)` |

| Format | Fields | Total bits | Comments |
|---|---|---|---|
| **R-format** | op (6 bits), rs (5 bits), rt (5 bits), rd (5 bits), shamt (5 bits), funct (6 bits) | 32 | Arithmetic instruction format |
| **I-format** | op (6 bits), rs (5 bits), rt (5 bits), address (16 bits) | 32 | Data transfer, branch format |

All MIPS instructions are 32 bits.

### 2.5 Logical Operation

Operations on selected bits within a word or on individual bits.

| Logic operations | C operators | Java operators | MIPS instructions |
|---|---|---|---|
| Shift left | `<<` | `<<` | `sll` |
| Shift right | `>>` | `>>>` | `srl` |
| Bit-by-bit AND | `&` | `&` | `and, andi` |
| Bit-by-bit OR | `\|` | `\|` | `or, ori` |
| Bit-by-bit NOT | `~` | `~` | `nor` |

### Shift operator

Move all the bits in a word to the left or right, filling emptied bits with 0.

Shifting left by *i* is the same result as multiplying by 2<sup>*i*</sup>.

```text
0000 0000 0000 0000 0000 0000 0000 1001    (9)₁₀
Shift left 4 ←
0000 0000 0000 0000 0000 0000 1001 0000    (9 × 16 = 144)₁₀
```

```asm
sll $t2, $s0, 4   # reg $t2 = reg $s0 << 4 bits
```

| op | rs | rt | rd | shamt | funct |
|---|---|---|---|---|---|
| 0 | 0 | 16 | 10 | 4 | 0 |

### OR operator

It is bit-by-bit.

- Result = 1 if **either** operand bit is 1.

```text
$t2: 0000 0000 0000 0000 0000 1101 0000 0000
$t1: 0000 0000 0000 0000 0011 1100 0000 0000

or $t0, $t1, $t2   # reg $t0 = reg $t1 | reg $t2

Result:
0000 0000 0000 0000 0011 1101 0000 0000
```

### NOR operator

- **NOT(A OR B)**
- A NOR 0 = NOT(A OR 0) = **NOT(A)**

```text
$t1: 0000 0000 0000 0000 0011 1100 0000 0000
$t3: 0000 0000 0000 0000 0000 0000 0000 0000

nor $t0, $t1, $t3   # reg $t0 = ~(reg $t1 | reg $t3)

Result:
1111 1111 1111 1111 1100 0011 1111 1111
```

## MIPS operands

| Name | Example | Comments |
|---|---|---|
| **32 registers** | `$s0, $s1, …, $s7`<br>`$t0, $t1, …, $t7` | Fast locations for data. In MIPS, data must be in registers to perform arithmetic. Registers `$s0-$s7` map to 16-23 and `$t0-$t7` map to 8-15. |
| **2³⁰ memory words** | `Memory[0]`, `Memory[4]`, …, `Memory[4294967292]` | Accessed only by data transfer instructions in MIPS. MIPS uses byte addresses, so sequential word addresses differ by 4. Memory holds data structures, arrays, and spilled registers. |

## MIPS assembly language

| Category | Instruction | Example | Meaning | Comments |
|---|---|---|---|---|
| **Arithmetic** | add | `add $s1, $s2, $s3` | `$s1 = $s2 + $s3` | Three register operands |
| | subtract | `sub $s1, $s2, $s3` | `$s1 = $s2 - $s3` | Three register operands |
| | Add immediate | `addi $s1, $s2, 100` | `$s1 = $s2 + 100` | + constants; overflow detected |
| **Data transfer** | load word | `lw $s1, 100($s2)` | `$s1 = Memory[$s2 + 100]` | Data from memory to register |
| | store word | `sw $s1, 100($s2)` | `Memory[$s2 + 100] = $s1` | Data from register to memory |
| **logical** | and | `and $s1, $s2, $s3` | `$s1 = $s2 & $s3` | three reg. operands; bit-by-bit AND |
| | or | `or $s1, $s2, $s3` | `$s1 = $s2 \| $s3` | three reg. operands; bit-by-bit OR |
| | nor | `nor $s1, $s2, $s3` | `$s1 = ~($s2 \| $s3)` | three reg. operands; bit-by-bit NOR |
| | and immediate | `andi $s1, $s2, 100` | `$s1 = $s2 & 100` | Bit-by-bit AND reg with constant |
| | or immediate | `ori $s1, $s2, 100` | `$s1 = $s2 \| 100` | Bit-by-bit OR reg with constant |
| | shift left logical | `sll $s1, $s2, 10` | `$s1 = $s2 << 10` | Shift left by constant |
| | shift right logical | `srl $s1, $s2, 10` | `$s1 = $s2 >> 10` | Shift right by constant |
