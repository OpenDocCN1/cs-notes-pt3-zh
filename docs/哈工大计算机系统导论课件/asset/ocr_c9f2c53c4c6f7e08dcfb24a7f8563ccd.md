# 移位指令汇总

| 移位类型 | 左移 | 右移 |
|---|---|---|
| 逻辑移位 | SHL CF | SHR 0 CF |
| 算术移位 | SAL CF | SAR CF |
| 循环移位 | ROL CF | ROR CF |
| 带有进位循环移位 | RCL CF | RCR CF |
| 双精度移位 | SHLD CF 目的操作数 源操作数 | SHRD 源操作数 目的操作数 CF |

所有指令都影响CF和OF