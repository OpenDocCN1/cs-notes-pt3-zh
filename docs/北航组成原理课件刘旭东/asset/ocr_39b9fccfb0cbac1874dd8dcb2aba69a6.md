# 2.4 8086/8088指令系统·指令格式与编码

# 一般双操作数指令格式与编码（续）

➢ **MOD和R/M：** 确定另外一个操作数。

| R/M | 存储器操作数有效地址(EA)：MOD=00 | MOD=01 | MOD=10 | 寄存器操作数：MOD=11，W=1 | W=0 |
|---|---|---|---|---|---|
| 000 | (BX)+(SI) | (BX)+(SI)+Disp8 | (BX)+(SI)+Disp16 | AX | AL |
| 001 | (BX)+(DI) | (BX)+(DI)+Disp8 | (BX)+(DI)+Disp16 | CX | CL |
| 010 | (BP)+(SI) | (BP)+(SI)+Disp8 | (BP)+(SI)+Disp16 | DX | DL |
| 011 | (BP)+(DI) | (BP)+(DI)+Disp8 | (BP)+(DI)+Disp16 | BX | BL |
| 100 | (SI) | (SI)+Disp8 | (SI)+Disp16 | SP | AH |
| 101 | (DI) | (DI)+Disp8 | (DI)+Disp16 | BP | CH |
| 110 | Disp16 | (BP)+Disp8 | (BP)+Disp16 | SI | DH |
| 111 | (BX) | (BX)+Disp8 | (BX)+Disp16 | DI | BH |

| Opcode | d | W | MOD | REG | R/M | Disp_Low | Disp_High | Imme. Data_Low | Imme. Data_High |
|---|---|---|---|---|---|---|---|---|---|