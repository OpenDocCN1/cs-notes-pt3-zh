# ARM状态下的寄存器组织

| 工作模式： | System&User | FIQ | Supervisor | Abort | IRQ | Undefined |
|---|---|---|---|---|---|---|
| 未分组寄存器 | R0 | R0 | R0 | R0 | R0 | R0 |
|  | R1 | R1 | R1 | R1 | R1 | R1 |
|  | R2 | R2 | R2 | R2 | R2 | R2 |
|  | R3 | R3 | R3 | R3 | R3 | R3 |
|  | R4 | R4 | R4 | R4 | R4 | R4 |
|  | R5 | R5 | R5 | R5 | R5 | R5 |
|  | R6 | R6 | R6 | R6 | R6 | R6 |
|  | R7 | R7 | R7 | R7 | R7 | R7 |
| 分组寄存器 | R8 | *R8_fiq* | R8 | R8 | R8 | R8 |
|  | R9 | *R9_fiq* | R9 | R9 | R9 | R9 |
|  | R10 | *R10_fiq* | R10 | R10 | R10 | R10 |
|  | R11 | *R11_fiq* | R11 | R11 | R11 | R11 |
|  | R12 | *R12_fiq* | R12 | R12 | R12 | R12 |
| 堆栈指针 | R13_usr | *R13_fiq* | *R13_svc* | *R13_abt* | *R13_irq* | *R13_und* |
| 链接寄存器 | R14_usr | *R14_fiq* | *R14_svc* | *R14_abt* | *R14_irq* | *R14_und* |
| 程序计数器 | R15(PC) | R15(PC) | R15(PC) | R15(PC) | R15(PC) | R15(PC) |
| 当前程序状态寄存器 | CPSR | CPSR | CPSR | CPSR | CPSR | CPSR |
| 备份程序状态寄存器 |  | *SPSR_fiq* | *SPSR_svc* | *SPSR_abt* | *SPSR_irq* | *SPSR_und* |