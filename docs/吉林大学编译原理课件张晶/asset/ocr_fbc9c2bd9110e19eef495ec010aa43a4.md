# 考虑寄存器分配的(+ ,A,B,t)的代码生成

| (+, A, B, T) | B不在寄存器且不活跃 | B不在寄存器且活跃 | B在寄存器R_B |
|---|---|---|---|
| A不在寄存器 | Load B, R_B
Add A, R_B | Load A, R_A
Load B, R_B
Add R_B, R_A | Load A, R_A
Add R_B, R_A |
| A在寄存器R_A | Add B, R_A | Load B, R_B
Add R_B, R_A | Add R_B, R_A |