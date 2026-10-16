# 一、8086/8088指令格式

HYPer

# 双操作数指令

操作码
寻址方式
OP(6) D(1) W(1) MOD(2) REG(3) R/M(3) Disp-L 或 Data-L Disp-H 或 Data-H Data-L Data-H

| REG | W=0 | W=1 | R/M | MOD=00 | MOD=01 | MOD=10 | MOD=11 |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  | W=0 | W=1 |
| 000 | AL | AX | 000 | BX+SI | BX+SI+Disp8 | BX+SI+Disp16 | AL | AX |
| 001 | CL | CX | 001 | BX+DI | BX+DI+Disp8 | BX+DI+Disp16 | CL | CX |
| 010 | DL | DX | 010 |  |  |  | DL | DX |
| 011 | BL | BX | 011 | BP+SI | BP+SI+Disp8 | BP+SI+Disp16 | BL | BX |
| 100 | AH | SP | 100 | BP+DI | BP+DI+Disp8 | BP+DI+Disp16 |  |  |
| 101 | CH | BP | 101 | SI | SI+Disp8 | SI+Disp16 | AH | SP |
| 110 | DH | SI | 110 | DI | DI+Disp8 | DI+Disp16 | CH | BP |
| 111 | BH | DI | 111 |  |  |  | DH | SI |
| D=1 | 目标操作数 |  |  | 源操作数 |  |  |  |  |
| D=0 | 源操作数 |  |  | 目标操作数 |  |  |  |  |