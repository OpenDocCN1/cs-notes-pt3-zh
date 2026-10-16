
## 1.6.1 Operand Addressing Modes
### Memory Operands Addressing
+ Specifying an Offset

The offset which results from adding displacement, base, index and scale factor is called an effective address(EA).

```
EA=Base + ( Index*Scale factor ) + Displacement
```

| components | 16-bit offset | 32-bit offset |
|---|---|---|
| displacement | 0,8,16-bit | 0, 8, 32-bit |
| Base Register | BX, BP | Any 32-bit general purpose registers |
| Index Register | SI, DI | 32-bit general purpose registers except ESP |
| Scale factor | Not used | 1, 2, 4, 8 |

## 1.6.1 Operand Addressing Modes
### Memory Operands Addressing
+ Direct Data Addressing

The EA of the operand in the instruction.

Segment Address
Instruction
EA
Memory
Operand
physical address = segment address ×16 + offset

```
MOV AX, [2000H]    ; Direct Addressing
```

```
MOV AX, 2000H      ; Immediate Addressing
```

### Direct Data Addressing Example1

MOV AX, [1000H]
(DS)=10A0H

Physical address

10A00H
+ 1000H
--------
11A00H

LSB

CODE
SEGMENT

OP

00H

10H

DATA
SEGMENT

11A00H

30H

50H

50H 30H AX

### Direct Data Addressing Example2

MOV BL, ES:[0100H]

(ES)=3000H
(DS)=2000H

![](img/d7c975450dfbe59120092c2721be78c6_64_0.png)

In assembly language, you can use symbols address to instead of numerical address, like this:

```
MOV AX, BUFF
or  MOV AX, [BUFF]
```

## 1.6.1 Operand Addressing Modes
### Memory Operands Addressing
### Register Indirect Addressing

The EA of the operand in register, register ID in the instruction.

![](img/d7c975450dfbe59120092c2721be78c6_65_0.png)

Example:
- MOV AL, [BX]
- MOV AX, CS:[SI]
- MOV [BP], AH
- MOV ECX, [EDX]

### Computer I/O System

MOV AH, [BP]
MOV BX, [SI]
MOV CX, SI

(SS)=1000H, (DS)=2000H, (BP)=0B10H, (SI)=032AH

| Physical address | Physical address |
|---|---|
| 10000H + 0B10H = 10B10H | 20000H + 032AH = 2032AH |

![](img/d7c975450dfbe59120092c2721be78c6_66_0.png)

### Example

MOV AX, 3000H[BX] (or [BX+3000H])

MOV AX, COUNT[BX] ; COUNT is Symbol address (or MOV AX, [COUNT+BX])

(DS)=3000H, (BX)=2000H, COUNT=4000H

30000H
2000H
+ 4000H
--------
36000H

36000H

34H
12H

1234H
AX

## 1.6.1 Operand Addressing Modes
### Memory Operands Addressing
### Register Relative Addressing
### Index-Plus-Displacement

- EA = displacement + contents of a base register.

![](img/d7c975450dfbe59120092c2721be78c6_69_0.png)

### Example

```
MOV CX, 6020H[SI] (or [SI+6020H])
```

```
MOV DX, COUNT[SI] ; COUNT is Symbol address
```

```
(or MOV AX, [COUNT+SI])
```

(DS)=3000H, (SI)=2000H, COUNT=1000H

30000H
2000H
+ 1000H
--------
33000H

![](img/d7c975450dfbe59120092c2721be78c6_70_0.png)

## 1.6.1 Operand Addressing Modes
### Memory Operands Addressing
### Base-Plus-Index Addressing

EA = contents of a base register + contents of a Index register.

![](img/d7c975450dfbe59120092c2721be78c6_71_0.png)

### Example:

```
MOV AX, [BX+DI]
MOV AX, [BX][DI]
```

(DS)=2100H, (BX)=0158H, (DI)=10A5H,

Physical address

21000H
0158H
+ 10A5H
--------
221FDH

221FDH
34H
12H

1234H
AX

## 1.6.1 Operand Addressing Modes
### Memory Operands Addressing
### Base Relative-Plus-Index Addressing

EA = contents of a base register + contents of a Index register + Displacement.

![](img/d7c975450dfbe59120092c2721be78c6_73_0.png)

## 1.6.1 Operand Addressing Modes
- Memory Operands Addressing
  - Scaled-Index Addressing

EA = contents of a Index register * scaling factor + Displacement.

![](img/d7c975450dfbe59120092c2721be78c6_75_0.png)

### Example:

MOV EAX, COUNT[ESI*4]

EA=ESI*4+COUNT
if (ESI)=3,(DS)=1000H
COUNT=2000H

Memory

![](img/d7c975450dfbe59120092c2721be78c6_76_0.png)

## 1.6.1 Operand Addressing Modes
### Memory Operands Addressing
### Scaled-Index Addressing

EA = contents of a base register + contents of a Index register * Scaling factor + Displacement.

Instruction

| Base Register ID | Index Register ID | Scaling factor | Displacement |
|---|---|---|---|
| Base Register ID | Index Register ID | Scaling factor | Displace ment |

Segment Address

memory

Index Register

Base Register

EA

Operand

Example:
MOV EAX, TABLE[EBX+EDI*4]
