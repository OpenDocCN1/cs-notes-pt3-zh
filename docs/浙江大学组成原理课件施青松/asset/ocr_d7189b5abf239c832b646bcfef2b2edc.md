# Truth Table for Main decoder

![](bbox=[0.033, 0.016, 0.976, 0.716])

| Instruction | RegDst | ALUSrc | MemtoReg | RegWrite | MemRead | MemWrite | Branch | ALUop1 | ALUop0 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| beq | X | 0 | X | 0 | 0 | 0 | 1 | 0 | 1 |
| R-format | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 1 | 0 |
| LW | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 0 |
| SW | X | 1 | X | 0 | 0 | 1 | 0 | 0 | 0 |