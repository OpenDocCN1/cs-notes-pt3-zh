

## 5.2 8254 的结构和引脚
### 操作和命令
### 控制字格式

| D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
| SC1 | SC0 | RW1 | RW0 | M2 | M1 | M0 | BCD |

SC — 选择计数器：

| SC1 | SC0 |  |
| 0 | 0 | 选择计数器 0 |
| 0 | 1 | 选择计数器 1 |
| 1 | 0 | 选择计数器 2 |
| 1 | 1 | 读回命令（参见读操作） |

RW — 读/写：

| RW1 | RW0 |  |
| 0 | 0 | 计数器锁存命令（参见读操作） |
| 0 | 1 | 仅读/写最低有效字节。 |
| 1 | 0 | 仅读/写最高有效字节。 |
| 1 | 1 | 先读/写最低有效字节，然后读/写最高有效字节。 |

M — 模式：

| M2 | M1 | M0 |  |
| 0 | 0 | 0 | 模式 0 |
| 0 | 0 | 1 | 模式 1 |
| X | 1 | 0 | 模式 2 |
| X | 1 | 1 | 模式 3 |
| 1 | 0 | 0 | 模式 4 |
| 1 | 0 | 1 | 模式 5 |

BCD：

|  |  |
| 0 | 二进制计数器 16 位 |
| 1 | 二进制编码十进制（BCD）计数器（4 位十进制） |

```
e.g.: MOV AL, 01110100B ; T/C1, least significant byte first
OUT 43H, AL ; mode 2, Binary
```

### 初始计数值

不同计数器的初始计数值必须写入不同的地址。

| A1A0 | 定时器/计数器 |
| 0 0 | T/C0 |
| 0 1 | T/C1 |
| 1 0 | T/C2 |

- 每次写入一个字节

- 初始计数值的范围是：

- 二进制：65536(0000H)、65535(FFFFH)~1(0001H)。

- BCD：10000(0000H)、9999(9999H)~1(0001H)。

### 初始化定时器/计数器

- 1) 对于每个计数器，在写入初始计数值之前必须先写入控制字。

- 2) 初始计数值必须遵循控制字中指定的计数格式

```
e.g. MOV AL, 01110101B; T/C1, least significant byte first, mode 2, BCD
OUT 43H, AL
MOV AX, 2000H ; initial count = 2000
OUT 41H, AL ;
MOV AL, AH
OUT 41H, AL ;
MOV AL, 00010110B; T/C0, least significant byte only, mode3, Binary
OUT 43H, AL
MOV AL, 50H ; ; initial count = 50H (80)
OUT 40H, AL
```

### 从 T/C 读数据的方法

计数器锁存命令（A1A0=11）

- CHB: D7D6=00~01, D5D4=00

e.g.:

```
MOV   AL, 01000101B  ; T/C1, latch, least significant
                         ; byte first, mode2, BCD
OUT   43H, AL
IN    AL, 41H
MOV   AH, AL
IN    AL, 41H
XCHG  AH, AL  ; AX is initial count for T/C1
```

- 从 T/C 读数据的方法

- 通过读回命令（A1A0=11）读取当前数据

| D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
|---|---|---|---|---|---|---|---|
| 1 | 1 | COUNT | STATUS | CNT 2 | CNT 1 | CNT 0 | 0 |

D5: 0 = 锁存所选计数器(s)的计数值

D4: 0 = 锁存所选计数器(s)的状态

D3: 1 = 选择计数器 2

D2: 1 = 选择计数器 1

D1: 1 = 选择计数器 0

D0: 保留供将来扩展；必须为 0

- 计数锁存命令只能锁存一个计数器

- 读回命令可以同时锁存多个计数器

```
e.g.: MOV AL, 11010100B    ; T/C1
OUT 43H, AL
IN  AL, 41H;
MOV AH, AL
IN  AL, 41H
XCHG AH, AL            ; AX is current count of CT1
MOV AL, 11011010B       ; T/C0 and T/C2
OUT 43H, AL
IN  AL, 40H;
MOV AH, AL
IN  AL, 40H
XCHG AH, AL            ; AX is current count of CT0
MOV BX, AX             ;
IN  AL, 42H;
MOV AH, AL
IN  AL, 42H
XCHG AH, AL            ; AX is current count of CT2
```

- 从 T/C 读数据的方法

- 通过读回命令(A1A0=11)读取状态

- 状态字

| D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
|---|---|---|---|---|---|---|---|
| OUTPUT | NULL COUNT | RW1 | RW0 | M2 | M1 | M0 | BCD |

D7 1 = 输出引脚为 1
0 = 输出引脚为 0
D6 1 = 空计数
0 = 计数值可供读取
D5-D0 计数器编程模式

```
MOV AL, 11100100B ; T/C1, latch the state
OUT 43H, AL
```

```
IN AL, 41H ; Suppose AL=00110101, means T/C1 in mode 2 ; BCD, least significant byte first, out pin = 0
```

```
MOV AL, 11100010B ; T/C0, latch the state
OUT 43H, AL
```

```
IN AL, 40 ; if AL=00010110, means T/C0 in mode 3, Binary ; least significant byte only, out pin = 0
```

