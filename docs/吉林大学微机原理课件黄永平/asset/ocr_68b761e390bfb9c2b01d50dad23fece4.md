# 1. 通用数据传送指令

HYPer

# (1) 基本传送指令 MOV d, s ;d←s

源操作数s——寄存器、存储器、立即数

目的操作数d——寄存器、存储器

执行的操作： d ← s

Move
Copy from d to s

# Data

Rc

M

Rs (cs不可变)

Mea= [BP
BX] + [SI
DI] + [Disp8
Disp16]

等宽传送原则