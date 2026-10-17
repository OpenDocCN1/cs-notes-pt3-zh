# # Designing the ALU decoder (Second level)

+   - Must describe hardware to compute 3-bit ALU control input

| Instruction opcode | ALUop | Instruction operation | Funct field | Desired ALU action | ALU control Input |
|---|---|---|---|---|---|
| LW | 00 | Load word | xxxxxx | Load word | 0010 |
| SW | 00 | Store word | xxxxxx | Store word | 0010 |
| Beq | 01 | branch equal | xxxxxx | branch equal | 0110 |
| R-type | 10 | add | 100000 | add | 0010 |
| R-type | 10 | subtract | 100010 | subtract | 0110 |
| R-type | 10 | AND | 100100 | AND | 0000 |
| R-type | 10 | OR | 100101 | OR | 0001 |
| R-type | 10 | Set on less than | 101010 | Set on less than | 0111 |