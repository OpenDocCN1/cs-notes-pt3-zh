

# 4.3 x86 系统中的中断

## 中断和异常分类

- 软件产生中断
- 常见中断指令

| 向量号 | 功能 | 向量号 | 功能 |
|---|---|---|---|
| 10H | 视频服务 | 13H | 磁盘控制 |
| 14H | COM | 15H | IO 外设 |
| 16H | 键盘 | 17H | LPT |
| 20H | 返回到 DOS | 21H | DOS 系统调用 |
| 23H | Ctrl+Break | 24H | DOS 严重错误 |
| 33H | 鼠标 | 2FH | DOS 保护模式接口 |
|  |  | 31H |  |

## 异常

### 软件产生异常

- INTO、INT 3 和 BOUND 指令允许在软件中产生异常。

### 机器检查异常

- P6 系列和 Pentium 处理器提供内部和外部机器检查机制，用于检查内部芯片硬件和总线事务的操作。

- 这些机制取决于实现。

- 当检测到机器检查错误时，处理器会发出机器检查异常（向量 18）并返回错误代码。

## PCH 中的 8259A

两个级联的 8259A 共 15 个中断

![](img/d7c975450dfbe59120092c2721be78c6_387_0.png)

- 两个级联的 8259A 共 15 个中断

- 初始化主控制器

```
INTM00    EQU    020H    ; Master 8259A port 0
INTM01    EQU    021H    ; Master 8259A port 1
......
MOV AL, 00010001B ; ICW1: edge trigger, ICW4 needed, cascaded, need ICW3
OUT INTM00, AL
JMP SHORT $+2    ; delay
MOV AL, 00001000B ; ICW2: interrupt vector number of IR0 is 08H
OUT INTM01, AL
JMP SHORT $+2
MOV AL, 00000100B ; ICW3: INT signal of slave connect on IR2 pin in master
OUT INTM01, AL
JMP SHORT $+2
MOV AL, 00010001B ; ICW4: Non buffered, special full nested, EOI
OUT INTM01, AL
JMP SHORT $+2
```

- 两个级联的 8259A 共 15 个中断

初始化从控制器

```
INTS00      EQU    0A0H    ; Slave 8259A port 0
INTS01      EQU    0A1H    ; Slave 8259A port 1
......
MOV AL, 00010001B ;ICW1:edge trigger, ICW4 needed, cascaded, need ICW3
OUT INTS00, AL
JMP SHORT $+2
MOV AL, 01110000B ;ICW2: interrupt vector number of IR0 is 70H
OUT INTS01, AL
JMP SHORT $+2
MOV AL, 00000010B ;ICW3: INT signal of slave connect on IR2 pin in master
OUT INTS01, AL
JMP SHORT $+2
MOV AL, 00000001B ;ICW4: Non buffered, special full nested, EOI
OUT INTS01, AL
JMP SHORT $+2
```

### 中断控制器核心连接

| 8259 | 8259 典型输入 | 典型中断源 | 连接引脚 / 功能 |
|---|---|---|---|
| 主 | 0 | 内部 | 内部定时器 / 计数器 0 输出 / HPET #0 |
| 主 | 1 | 键盘 | 使用 SERIRQ 的 IRQ1 |
| 主 | 2 | 内部 | 从控制器 INTR 输出 |
| 主 | 3 | 串口 A | 使用 SERIRQ、PIRQ# 的 IRQ3 |
| 主 | 4 | 串口 B | 使用 SERIRQ、PIRQ# 的 IRQ4 |
| 主 | 5 | 并口 / 通用 | 使用 SERIRQ、PIRQ# 的 IRQ5 |
| 主 | 6 | 软盘 | 使用 SERIRQ、PIRQ# 的 IRQ6 |
| 主 | 7 | 并口 / 通用 | 使用 SERIRQ、PIRQ# 的 IRQ7 |

![](img/d7c975450dfbe59120092c2721be78c6_390_0.png)

- PCH 中的 8259A
  - 在 Intel 芯片组中设置中断请求模式
    - 在 PCH 中，ICW1 中的 bit3 被禁用，并新增一个用于边沿和电平触发模式选择的寄存器。

ELCR1——用于主控制器（地址 4D0H）

| 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|---|---|---|---|---|---|---|---|
| IRQ7 | IRQ6 | IRQ5 | IRQ4 | IRQ3 | 0 | 0 | 0 |

ELCR2——用于从控制器（地址 4D1H）

| 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|---|---|---|---|---|---|---|---|
| IRQ15 | IRQ14 | 0 | IRQ12 | IRQ11 | IRQ10 | IRQ9 | 0 |

IRQx=0 : IRQx 为边沿触发模式

IRQx=1 : IRQx 为电平触发模式

