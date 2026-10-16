
## (2)带符号乘法 IMUL s ;AX ← AL * s
;DX AX ← AX * s

s = Rc -- - M

Signed multiply

注：

- 该指令影响标志位
- 若结果的高半部分不是低半部分的符号扩展的话，

则 C=1, O=1
否则 C=0, O=0

![](img/d63acdb9d192b1c4466c984c4275a5a3_224_0.png)

## 符号扩展：

从8位扩展到16位  ±20H

+20H      0010,0000  →  0000,0000,0010,0000

-20H      1111,1110  →  1111,1111,1111,1110

符号位

例：  MOV AL, 0B4H

MOV BL, 11H

MUL BL

## 4.除法指令

HYPer

### (1)无符号除法 DIV s
;AH(余),AL(商) ← AX/s ,s为字节(8位)
;DX(余),AX(商) ← DX AX / s ,s为字(16位)

s = Rc --- -- - M

![](img/d63acdb9d192b1c4466c984c4275a5a3_226_0.png)

注：

- 该指令不影响标志位
- s的类型决定是字或字节相除

## (2)有符号除法 IDIV s

;AH(余),AL(商) ← AX/s ,s为字节(8位)

;DX(余),AX(商) ← DX AX / s ,s为字(16位)

s = Rc --- -M

![](img/d63acdb9d192b1c4466c984c4275a5a3_227_0.png)

注：

- 该指令不影响标志位

- s的类型决定是字或字节相除

- 有符号除之前要进行符号位扩展,用CBW, CWD

## (3)字节到字符号位扩展 CBW

;AH ← AL符号位，即AL₇=0时，AH=0； AL₇=1， AH=0FFH

![](img/d63acdb9d192b1c4466c984c4275a5a3_228_0.png)

## (4)字到双字符号位扩展 CWD

;DX ← AX符号位，即AX₁₅=0时，DX=0； AX₁₅=1， DX=0FFFFH

该指令不影响标志位

![](img/d63acdb9d192b1c4466c984c4275a5a3_228_1.png)

## 5. 十进制调整指令

### (1). 十进制数的表示

BCD码——用4位二进制编码的十进制数。

| 类型 | 编码 | 数值 |
|---|---|---|
| 压缩BCD | 0000　0001　0010　0011　0100　0101　0110　0111　1000　1001 | 0　1　2　3　4　5　6　7　8　9 |
| 非压缩BCD | UUUU0000　UUUU0001　UUUU0010　……　UUUU1001 | 0　1　2　9 |

### (2). 调整原理

以加法调整为例。

7
+ 6
13

0111
+ 0110
1101
D

1101
+ 0110
1 0011
0001 0011
13 (H)

不同的运算指令的调整方法不同，但道理是一样的。

### (3). 调整指令

加法： DAA 压缩的BCD码加法十进制调整指令。

AAA 非压缩的BCD码加法十进制调整指令。

减法： DAS 压缩的BCD码减法十进制调整指令。

AAS 非压缩的BCD码减法十进制调整指令。

乘法： AAM 非压缩的BCD码乘法十进制调整指令。

除法： AAD 非压缩的BCD码除法十进制调整指令。

### (3). 调整指令

### Decimal Adjust after Addition

#### (a)压缩BCD码加法调整指令 DAA

; AL7 AL6 AL5 AL4 AL3 AL2 AL1 AL0

高 nibble：>9 或 CF = 1 → +6
低 nibble：>9 或 AF = 1 → +6

压缩BCD码 + 压缩BCD码 → BCD码
DAA调整

### (3). 调整指令

#### (b)压缩BCD码减法调整指令 DAS

; AL7 AL6 AL5 AL4 AL3 AL2 AL1 AL0

> 9 或 CF = 1 - 6

> 9 或 AF = 1 - 6

压缩BCD码 - 压缩BCD码 → BCD码

DAS调整

Decimal Adjust After Subtraction

### (3). 调整指令

### ASCII Adjust after Addition

#### (c)非压缩BCD码加法调整指令 AAA

; AL₇ AL₆ AL₅ AL₄ AL₃ AL₂ AL₁ AL₀

清0

>9 或 AF = 1

+ 6 并且 AH ← AH+1 并且 CF ← 1

非压缩BCD码 + 非压缩BCD码 → 非压缩BCD码

AAA调整

结果在AH AL中，以非压缩BCD码形式存贮

### （3）调整指令

#### （d）非压缩BCD码减法调整指令 AAS

; AL₇ AL₆ AL₅ AL₄ AL₃ AL₂ AL₁ AL₀

清0

{ >9 或 AF = 1 }

− 6
并且
AH ← AH − 1
并且
CF ← 1

非压缩BCD码  −  非压缩BCD码  →  非压缩BCD码（AH AL）

AAS调整

结果在AH AL中，以非压缩BCD码形式存储

![](img/d63acdb9d192b1c4466c984c4275a5a3_235_0.png)

### (3). 调整指令

#### (e)非压缩BCD码乘法调整指令 AAM

; AH ← AL/10 的商, AL ← AL/10 的余数

ASCII Adjust after Multiplication

非压缩BCD码 * 非压缩BCD码

非压缩BCD码 (AH AL)

AAM调整

高4位清0

例：
AND AL, 0FH
AND BL, 0FH
MUL BL
AAM

结果在AH AL中，以非压缩BCD码形式存贮

### （3）调整指令

#### （f）非压缩BCD码除法调整指令  AAD

```
`; AL ← AH * 10 + AL`
```

AH中放非压缩BCD码，AL中放非压缩BCD码，先进行AAD，把它变为二进制数据在AL中，之后进行DIV运算。

![](img/d63acdb9d192b1c4466c984c4275a5a3_237_0.png)

## 四、逻辑运算指令

![](img/d63acdb9d192b1c4466c984c4275a5a3_238_0.png)

| 分类 | 名称 | 格式 | 功能 | O S Z A P C |
|---|---|---|---|---|
| 逻辑运算指令 | 逻辑与指令 | AND d, s | 与（字、字节） | O S Z   P C |
| 逻辑运算指令 | 逻辑或指令 | OR d, s | 或（字、字节） | O S Z   P C |
| 逻辑运算指令 | 逻辑非指令 | NOT d | 非（字、字节） | 不影响 |
| 逻辑运算指令 | 逻辑异或指令 | XOR d, s | 异或（字、字节） | O S Z   P C |
| 逻辑运算指令 | 测试指令 | TEST d, s | 测试（字、字节） | O S Z   P C |
| 移位指令 | 逻辑左移指令 | SHL d, count | 逻辑左移（字、字节） | O S Z   P C |
| 移位指令 | 算术左移指令 | SAL d, count | 算术左移（字、字节） | O S Z   P C |
| 移位指令 | 逻辑右移指令 | SHR d, count | 逻辑右移（字、字节） | O S Z   P C |
| 移位指令 | 算术右移指令 | SAR d, count | 算术右移（字、字节） | O S Z   P C |
| 循环移位指令 | 循环左移指令 | ROL d, count | 循环左移(字,字节) | O       C |
| 循环移位指令 | 循环右移指令 | ROR d, count | 循环右移(字,字节) | O       C |
| 循环移位指令 | 带进位循环左移指令 | RCL d, count | 带来循环左移(字,字节) | O       C |
| 循环移位指令 | 带进位循环右移指令 | RCR d, count | 带来循环右移(字,字节) | O       C |

## # 1.逻辑运算指令

注: 该指令影响标志位 使 0=0,C=0, P,S,Z反映操作的结果。

![](img/d63acdb9d192b1c4466c984c4275a5a3_239_0.png)

![](img/d63acdb9d192b1c4466c984c4275a5a3_239_1.png)

> Logical AND

## 例1：屏蔽AL寄存器的低四位。

```
MOV AL, 0FFh
AND AL, 0F0h
```

11111111
∧ 11110000
---------
11110000

使一立即数的该位为0即可

## 例2：屏蔽AL寄存器的高两位。

```
MOV AL, 0FFh
AND AL, 3Fh
```

11111111
∧ 00111111
---------
00111111

使一立即数的该位为0即可

AND通常用于使某些位置0，其它位不变的情况。
