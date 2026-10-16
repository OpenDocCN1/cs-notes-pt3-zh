# 通用寄存器

AH AL AX
BH BL BX
CH CL CX
DH DL DX
SP
BP
SI
DI

# 地址加法器

CS
DS
SS
ES
IP
内部寄存器

20位

16位 10 10 3

# 输入/输出控制电路

总线

10100 A0
10101 00
10102 20
04
02
F4

代码段 CS

30000
32000 10
32001 20

数据段 DS

堆栈段 SS

# ALU

# 执行部分 地址控制

# 标志寄存器

16位 10

8位 1 2 3 4 5 6

# 指令队列缓冲器

执行部分（EU）

总线接口部分（BIU）

内存

A0h 00h 20h MOV AL,[2000]
04h 02h ADD AL,02
F4h HLT