

## 2.6.2 算术指令
### 加法、减法和比较
### 带进位加法

```
ADC DST, SRC
```

DST ← (DST) + (SRC) + Carry

该指令会影响 CF、SF、OF、PF、ZF 和 AF

### 递增加法

```
INC DST
```

DST ← (DST) + 1

该指令会影响 SF、OF、PF、ZF 和 AF，对 CF 无影响

| 符号 | 示例 |
|---|---|
| INC reg8/16/32 | INC CX |
| INC mem8/16/32 | INC BYTE PTR[BX] |

### ADC 示例——8086 中的双字加法

假设为 8086 编写程序，将 DX 和 AX 中的 32 位数加到 BX 和 CX 中的 32 位数

![](img/d7c975450dfbe59120092c2721be78c6_169_0.png)

```
ADD AX, CX   ; add low word
ADC DX, BX   ; add high word
```

### INC 示例

```
LEA EBX, ARRAY
MOV AL, [BX]
......
INC BX
```

```
MOV BX, 0
MOV AL, ARRAY[BX]
......
INC BX
```

![](img/d7c975450dfbe59120092c2721be78c6_170_0.png)

if DX:AX=37A1FFFFH, then can we use

```asm
INC AX
ADC DX,0
```

to do DX:AX+1?

### 加法、减法和比较
### 减法指令

```
SUB DST, SRC
```

DST←(DST) - (SRC)

该指令会影响 CF、SF、OF、PF、ZF 和 AF

| 符号 | 示例 |
|---|---|
| SUB reg8/16/32, imm8/16/32 | SUB AX,837FH |
| SUB reg8/16/32, reg8/16/32 | SUB EAX, EBX |
| SUB reg8/16/32, mem8/16/32 | SUB CX, WORD PTR[SI] |
| SUB mem8/16/32, reg8/16/32 | SUB BYTE PTR[DI],DL |
| SUB mem8/16/32, imm8/16/32 | SUB BYTE PTR[DI], 23 |

### SUB 示例

SUB BX, CX

执行前

(BX)=9543H    (CX)=28A7H

9543H
- 28A7H
------
6C9CH

执行后：

(BX)=6C9CH

CF=0   OF=1   ZF=0   SF=0

### 加法、减法和比较
### 带借位减法

```
SBB DST, SRC
```

DST <-- (DST) - (SRC) - Carry

该指令会影响 CF、SF、OF、PF、ZF 和 AF

### SBB 示例

```
SUB AX, CX    ; sub low word
```

```
SBB DX, BX    ; sub high word
```

7456H AX
- 9428H CX
1 E11EH

0012H DX
0010H BX
- 1H CF
0001H

CF=1

### 加法、减法和比较
### 递减减法

```
DEC DST
```

DST←(DST) - 1

该指令会影响 SF、OF、PF、ZF 和 AF，对 CF 无影响

### 二进制补码

```
NEG DST;
```

DST←0-(DST)

| 符号 | 示例 |
|---|---|
| DEC reg/mem8/16/32 | DEC CX ; DEC BYTE PTR[SI] |
| NEG reg/mem8/16/32 | NEG WORD PTR[DI] |

### NEG 示例1

NEG DX

执行前：
(DX)=6780H

![](img/d7c975450dfbe59120092c2721be78c6_175_0.png)

执行后：
(DX)=9880H    CF=1

### NEG 示例2

NEG AL       ; 0-(AL)
ADD AL, 100   ; (AL)+100-->AL

实现：    100-(AL)

### 加法、减法和比较
### 比较指令

```
CMP DST, SRC
```

- (DST) – (SRC)
- 该指令会影响 CF、SF、OF、PF、ZF 和 AF
- DST 永不改变

| 符号 | 示例 |
|---|---|
| CMP reg8/16/32, imm8/16/32 | CMP AX,837FH |
| CMP reg8/16/32, reg8/16/32 | CMP EAX, EBX |
| CMP reg8/16/32, mem8/16/32 | CMP CX, WORD PTR[SI] |
| CMP mem8/16/32, reg8/16/32 | CMP BYTE PTR[DI],DL |
| CMP mem8/16/32, imm8/16/32 | CMP BYTE PTR[DI], 23 |

### 加法、减法和比较
### 比较指令 (CMP)

CMP 通常后跟条件跳转指令，该指令测试标志位的状态。

- 对于无符号比较
  - if ZF=1, then DST = SRC
  - if CF=0, then DST ≥ SRC
  - if CF=1, then DST < SRC

- 对于有符号比较
  - if ZF=1, then DST = SRC
  - if SF=OF, then DST ≥ SRC
  - if SF<>OF, then DST < SRC

### CMP 示例1

CMP AL, BL

(AL)=-64    (BL)=10

- 64
- 10
------
- 74

OF=0  SF=1

结果： (DST)<(SRC)

### CMP 示例2

CMP CL, [100H]

(CL)=-100    (DS:100)=-110

-100
- (-110)
------
10

OF=0  SF=0

结果： (DST)>(SRC)

