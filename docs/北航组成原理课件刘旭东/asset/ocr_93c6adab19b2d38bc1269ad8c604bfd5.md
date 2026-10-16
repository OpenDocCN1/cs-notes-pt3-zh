# Example

Y=ax²+bx-c  假定a,b,c,x均为已知数，且存放在内存中，求y。

假定指令系统：16位指令系统

| Opcode | Address |
| 8 | 8 |

| 指令 | 操作码 | 说明 |
| ADD | 00H | AC ← (AC)+Mem(Add) |
| LD | 01H | AC ← Mem(Add) |
| SUB | 02H | AC ← (AC) — Mem(Add) |
| MUL | 03H | AC ← (AC)×Mem(Add) |
| ST | 04H | Mem(Add) ← (AC) |

| 内存 | 地址 |
|  | 00H |
|  | 02H |
|  | 04H |
|  | 06H |
|  | 08H |
|  | 0AH |
|  | 0CH |
|  | 0EH |
| 结果y将存放在此 | 10H |
| 值a | 12H |
| 值b | 14H |
| 值c | 16H |
| 值x | 18H |