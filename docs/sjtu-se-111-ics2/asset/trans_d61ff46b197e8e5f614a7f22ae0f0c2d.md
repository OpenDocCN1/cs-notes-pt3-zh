

## 周期 3 结束

Cycle 3: 0x00c: addl %edx,%ebx   # %ebx←0x300 CC←000

+   - state set according to 2nd instruction
+   - combinational logic generates results for 3rd instruction

![](img/9bd5f6161cb6607b56d2fb964d1b8794_69_0.png)

## 周期 4 开始

![](img/9bd5f6161cb6607b56d2fb964d1b8794_70_0.png)

| Cycle | Instruction | Description |
|---|---|---|
| Cycle 1: | `0x000: irmovl $0x100,%ebx` | `%ebx←0x100` |
| Cycle 2: | `0x006: irmovl $0x200,%edx` | `%edx←0x200` |
| Cycle 3: | `0x00c: addl %edx,%ebx` | `%ebx←0x300  CC←000` |
| Cycle 4: | `0x00e: je dest` | `Not taken` |

## 周期 4 开始

Cycle 4: 0x00e: je dest # Not taken

+   - state set according to 3rd instruction
+     - PC: 0x00E
+     - CC: 000
+     - %edx: 0x200
+     - %ebx: 0x300
+   - combinational logic starting to react to state changes

![](img/9bd5f6161cb6607b56d2fb964d1b8794_71_0.png)

## 周期 4 结束

![](img/9bd5f6161cb6607b56d2fb964d1b8794_72_0.png)

```
Cycle 1: 0x000: irmovl $0x100,%ebx # %ebx←0x100
```

```
Cycle 2: 0x006: irmovl $0x200,%edx # %edx←0x200
```

```
Cycle 3: 0x00c: addl %edx,%ebx   # %ebx←0x300 CC←000
```

```
Cycle 4: 0x00e: je dest   # Not taken
```

## 周期 4 结束

Cycle 4: 0x00e: je dest # Not taken

+   - state set according to 3rd instruction
+   - combinational logic generates results for 4th instruction

![](img/9bd5f6161cb6607b56d2fb964d1b8794_73_0.png)

## 如何设计 SEQ ？

+   - Naïve Design: One-by-one
+     - Straightforward, but waste
+   - Advanced Design: Multi-stages
+     - Formulate instruction execution as sequence of simple steps (stages)
+       - Like: function for programming
+     - Best use of hardware
+     - Challenge: use same general form for all instructions

## Y86 指令解码

![](img/9bd5f6161cb6607b56d2fb964d1b8794_75_0.png)

+   - Instruction Format
+     - Instruction byte
+     - Optional register byte
+     - Optional constant word

icode:ifun
rA:rB
valC

## Y86 指令集

Byte
0 1 2 3 4 5
nop
0 0
halt
1 0
rrmovl rA,rB
2 0 rA rB
irmovl V,rB
3 0 F rB V
rmmovl rA,D(rB)
4 0 rA rB D
mrmovl D(rB),rA
5 0 rA rB D
OP1 rA, rB
6 fn rA rB
addl 6 0
subl 6 1
andl 6 2
xorl 6 3

## Y86 指令集

| Instruction | Encoding |
|---|---|
| `jXX Dest` | `7 fn` + `Dest` |
| `call Dest` | `8 0` + `Dest` |
| `ret` | `9 0` |
| `pushl rA` | `A 0 rA F` |
| `popl rA` | `B 0 rA F` |

Byte positions: `0 1 2 3 4 5`

Jump-function encodings:

| Instruction | Code |
|---|---|
| `jmp` | `7 0` |
| `jle` | `7 1` |
| `jl` | `7 2` |
| `je` | `7 3` |
| `jne` | `7 4` |
| `jge` | `7 5` |
| `jg` | `7 6` |

## 指令执行阶段

+   - Fetch
+     - Read instruction from instruction memory
+   - Decode
+     - Read program registers
+   - Execute
+     - Compute value or address
+   - Memory
+     - Read or write data
+   - Write Back
+     - Write program registers
+   - PC
+     - Update program counter

![](img/9bd5f6161cb6607b56d2fb964d1b8794_79_0.png)

PC

Write back

Memory

Data memory

Execute

CC

ALU

Decode

A B E Register File

Fetch

Instruction memory

PC increment

PC

## SEQ 硬件结构

+   - Instruction Flow
+     - Read instruction at address specified by PC: 1
+     - Process through stages: 2→5
+     - Update program counter: 6

## 执行算术/逻辑操作

opl rA, rB    6 fn rA rB

+   - Fetch
+     - Read 2 bytes
+   - Decode
+     - Read operand registers
+   - Execute
+     - Perform operation
+     - Set Condition Ccodes

+   - Memory
+     - Do nothing
+   - Write back
+     - Update register rB
+   - PC Update
+     - Increment PC by 2

## 阶段计算: 算术/逻辑操作

|  | OPl rA, rB |  |
|---|---|---|
| Fetch | icode:ifun ← M₁[PC]
rA:rB ← M₁[PC+1]

valP ← PC+2 | Read instruction byte
Read register byte

Compute next PC |
| Decode | valA ← R[rA]
valB ← R[rB] | Read operand A
Read operand B |
| Execute | valE ← valB ifun
Set CC | Perform ALU operation
Set condition code register |
| Memory |  |  |
| Write back | R[rB] ← valE | Write back result |
| PC update | PC ← valP | Update PC |

