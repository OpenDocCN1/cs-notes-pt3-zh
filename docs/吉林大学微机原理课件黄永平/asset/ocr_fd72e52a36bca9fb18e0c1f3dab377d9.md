# 一、8086/8088指令格式

# 3. 双操作数指令（R-R）

| 15 | 0 |
| OP(6) | D(1) | W(1) | MOD(2) | REG(3) | R/M(3) |
| MOD=11 |

D = REG为目标(R/M为源)/REG为源(R/M为目标)。指出目标、源寄存器的位置。

D=1时，REG中为目标操作数R，R/M为源操作数据R； D=0 相反。

REG，R/M都有8种组合， AL/AX,CL/CX,DL/DX,BL/BX,AH/SP,CH/BP,DH/SI,BH/DI.

W=字/字节选择(16位/8位)