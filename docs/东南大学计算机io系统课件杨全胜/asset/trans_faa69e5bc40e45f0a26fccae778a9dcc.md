

## 2.6.2 算术指令
## 乘法和除法

- 无符号乘法
  - `MUL SRC`
- 有符号乘法
  - `IMUL SRC`

| 符号 | 操作 |
|---|---|
| `MUL/IMUL reg/mem8` | `AX ← AL * reg/mem8` |
| `MUL/IMUL reg/mem16` | `DX:AX ← AX * reg/mem16` |
| `MUL/IMUL reg/mem32` | `EDX:EAX ← EAX * reg/mem32` |

### 无符号乘法

```
MUL SRC
```

### 有符号乘法

```
IMUL SRC
```

乘法后的乘积始终是双倍宽度的乘积。

该指令会影响 CF 和 OF

- CF=OF=1：表示乘积的高位半部分不为零
- CF=OF=0：表示乘积的高位半部分为零
- 对其他标志的改变无意义

## MUL, IMUL 示例

### MUL BL

(AL)=0B4H=180
(BL)=11H=17

1011 0100
× 0001 0001
1011 0100
1011 0100
1011 1111 0100

(AX)=0BF4H=3060

### IMUL BL

(AL)=0B4H= -76,
(BL)=11H=17
-76补=4CH

0100 1100
× 0001 0001
0100 1100
0100 1100
0101 0000 1100

(AX)=(-050C)补
=FAF4H= -1292

## 乘法和除法

### 一种特殊的带符号乘法

```
IMUL REG, SRC
IMUL REG, SRC, IMM
```

乘积、REG 和 SRC 尺寸相同，为 16 位或 32 位

| 符号 | 操作 |
|---|---|
| IMUL *reg16/32, reg/mem16/32* | Reg16/32=reg16/32*reg/mem16/32 |
| IMUL *reg16/32, reg/mem16/32, imm8* | Reg16/32=reg/mem16/32*sign-extended imm8 |
| IMUL *reg16, reg/mem16, imm16* | Reg16=reg/mem16*sign-extended imm16 |
| IMUL *reg32, reg/mem32, imm32* | Reg32=reg/mem32*sign-extended imm32 |

- 无符号除法
  - DIV SRC
- 有符号除法
  - IDIV SRC

| 符号 | 操作 |
|---|---|
| DIV/IDIV reg/mem8 | AX 除以 reg/mem8<br>AL←商, AH←余数 |
| DIV/IDIV reg/mem16 | DX:AX 除以 reg/mem16<br>AX←商, DX←余数 |
| DIV/IDIV reg/mem32 | EDX:EAX 除以 reg/mem32<br>EAX←商, EDX←余数 |

### 无符号除法
`DIV SRC`

### 有符号除法
`IDIV SRC`

### 除法过程中发生的错误

- 尝试除以零；
- 商过大，无法放入单长度的目的地
  - 2468AH ÷ 2 = 12345H
  - 0FFFFFFFH ÷ 1 = 0FFFFFFFFH

除法指令可能会破坏先前设置的 AF、CF、OF、PF、SF 和 ZF 的值，但未定义。

### 乘法和除法

- 无符号除法

```
DIV SRC
```

- 有符号除法

```
IDIV SRC
```

- 商的符号由被除数和除数的符号按照普通的符号规则确定；
- 余数的符号始终与被除数的符号相同

### ■ 乘法和除法

- ◆ 无符号除法
  `DIV SRC`
- ◆ 有符号除法
  `IDIV SRC`

被除数始终是双倍宽度的被除数
除以操作数。

- • 对于无符号除法，
  - 在高位扩展零
- • 对于有符号除法，
  - 将符号位扩展到高位

### 符号扩展指令

|  |  |
|---|---|
| CBW | : AL 到 AX |
| CWD | : AX 到 DX:AX |
| CWDE | : AX 到 EAX |
| CDQ | : EAX 到 EDX:EAX |

```
RESILT DB ?
.....
MOV AL, -127    ; Dividend(81H)
CBW             ; Byte extend to word
MOV BL, 15      ; Divisor
IDIV BL         ; -127/15
MOV RESULT, AL  ; Quotient
```

```
N1  WORD  ?
N2  WORD  ?

......
MOV  AX, 2012      ; Dividend=2012
MOV  DX, 0         ; Zero Extend to DX:AX
MOV  BX, 1000      ; Divisor = 1000
DIV  BX            ; 10000H/100H
MOV  N1, AX        ; Quotient
MOV  N2, DX        ; Remainder
```

假设 X、Y、Z、V 为 16 位有符号数，计算 (V-(X*Y+Z))/X。商在 AX，余数在 DX

```
MOV  AX, X
IMUL Y                 ; X*Y
MOV  CX, AX
MOV  BX, DX            ; store in BX: CX
MOV  AX, Z
CWD                    ; signed extend the Z
ADD  CX, AX            ; X*Y+Z
ADC  BX, DX
MOV  AX, V
CWD                    ; signed extend the V
SUB  AX, CX            ; -
SBB  DX, BX
IDIV X                 ; Divided by X
```
