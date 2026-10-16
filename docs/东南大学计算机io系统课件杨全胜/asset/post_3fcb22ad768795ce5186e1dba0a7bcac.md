
## 2.6.3 Logic Instructions
### AND Example

```
MOV AL, 32H
AND AL, 0FH        ; clear the high 4 bits in AL
```

|        | AL       |
|--------|----------|
| before execution | 00110010 |
| after execution  | 00000010 |

### OR Example

```
MOV AL, 02H
OR  AL, 0F0H       ; set the high 4 bits in AL
```

|        | AL       |
|--------|----------|
| before execution | 00000010 |
| after execution  | 11110010 |

### XOR Example

| Instruction | Value      |
|-------------|------------|
| MOV AL, 0B6H | 1011 0110 |
| XOR AL, 0FH  | 0000 1111 |
| Result       | 1011 1001 |

No change    Negate

## 2.6.3 Logic Instructions
### Basic Logic Instructions

```
TEST OPR1, OPR2 ; (OPR1) & (OPR2)
```

- The same as AND instruction but not change destination
- AND, OR, XOR, TEST will affect flag register.
  - CF=0
  - OF=0
  - AF: undefined
  - PF, SF, ZF: set by the value of result.

> **What’s the follow instructions mean?**
> 
> **AND AX,AX;** Clear the CF and OF in flag register
> 
> **XOR AX,AX;** AX=0, CF=0 and OF=0

## 2.6.3 Logic Instructions
### TEST Example

Determine whether (AL) is odd, if it’s true, jump

```
TEST AL, 01H
JNZ NEXT        ; ZF=0, jump
```

### TEST Example2

Determine whether (AX) is positive, if it’s true, jump

```
TEST AX, 8000H
JZ THERE        ; ZF=1转
```

## 2.6.3 Logic Instructions
### Basic Logic Instructions

NOT DST : not operation

- one's complement, Logic inversion.
- True Table
- NOT r/m8/16/32
- Not affect flag register

| A | T |
|---|---|
| 0 | 1 |
| 1 | 0 |

### NOT Example1

```
MOV AL, 52H
NOT AL
before  AL  01010010
after   AL  10101101
```

### NOT Example2

```
MOV AL, 1 ; 1-->AL
NOT AL ; 求反
INC AL ;
```

## 2.6.3 Logic Instructions
### Shift and Rotate Instruction

- Shift and rotate instructions manipulate binary numbers at the binary bit level, as did the AND, OR, Exclusive-OR, and NOT instructions.
- Shifts and rotates find their most common applications in low-level software used to control I/O devices.
- The microprocessor contains a complete set of shift and rotate instructions that are used to shift or rotate any memory data or register.

## 2.6.3 Logic Instructions
### Shift and Rotate Instruction
### Shift Instructions

```
OP DST, CNT; OP is SHL, SAL, SHR, SAR
```

SHL/SAL
logically/arithmetically
shift left

![](img/d7c975450dfbe59120092c2721be78c6_211_0.png)

SHR
Logically shift right

![](img/d7c975450dfbe59120092c2721be78c6_211_1.png)

SAR
Arithmetically shift right

![](img/d7c975450dfbe59120092c2721be78c6_211_2.png)

## 2.6.3 Logic Instructions
### Shift and Rotate Instruction
### ◆ Shift Instructions

Suppose (AL)=0B4H, (CF)=1, analyze the result after execution

| Instruction | CF | AL |
|---|---:|---|
| Before execution | 1 | 10110100 |
| (1) SAL AL, 1 | 1 | 01101000 |
| (2) SHL AL, 1 | 1 | 01101000 |
| (3) SAR AL, 1 | 0 | 11011010 |
| (4) SHR AL, 1 | 0 | 01011010 |

Both of the result of the shift left are the same.
Two kind of Arithmetically shift right get the different result.

## 2.6.3 Logic Instructions
### ■ Shift and Rotate Instruction
### ◆ Shift Instructions

Y is a number of byte, how to calculate (Y)*10?
We know: (Y)*10=(Y)*(8+2)=(Y)*2+(Y)*8 (Why do this?)

```
MOV AL, Y     ; AL<--(Y)
MOV AH, 0
SHL AX, 1      ; (Y)*2
MOV BX, AX
SHL AX, 1      ; (Y)*4
SHL AX, 1      ; (Y)*8
ADD AX, BX     ; (Y)*10
```

How to calculate DX=3×AX+7×BX by using shift instruction?

## 2.6.3 Logic Instructions
### Shift and Rotate Instruction

- Shift instructions will change flags:
  - CF: change by shifted bit
  - OF:
    - Multiple-bit shift: undefined
    - Single-bit shift
      - 0: if the sign bit of the result is the same as the sign bit of the original operand value.
      - 1: they are different
  - ZF, PF: assigned according to result
  - AF: undesigned
