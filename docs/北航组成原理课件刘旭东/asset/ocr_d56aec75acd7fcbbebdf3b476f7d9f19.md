# 3.3 微操作信号的综合

# ◆ IB ← MDR微操作控制信号的布尔表达式

| 指令 | IB←MDR有效的时间与条件 |  |  |  |  |
| --- | 时间节拍 | 操作码译码 | 源寻址译码 | 目寻址译码 | FR |
| 示例中的所有指令 | M1.T4 |  |  |  |  |
| MOV AX,1000H[BX] | M2.T4 | MOV | Sₓ | D_R |  |
| MOV 1000H[BX],AX | M2.T4 | MOV | S_R | Dₓ |  |
| ADD 2000H[BX],1000H | M2.T4 | ADD | S_imm | Dₓ |  |
|  | M3.T4 | ADD | S_imm | Dₓ |  |
|  | M4.T4 | ADD | S_imm | Dₓ |  |
| JNE 1200 | M2.T4 | JNE |  |  |  |

IB ← MDR = M₁T₄(OP_Mov + OP_Add + OP_Jne) + OP_Mov M₂T₄(SₓDᵣ + SᵣDₓ) + OP_Add S_imm Dₓ T₄(M₂ + M₃ + M₄) + OP_Jne M₂T₄