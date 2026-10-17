# 不同类型指令功能举例

+   - 例子：不同指令系统完成C=A+B的指令序列
+   - 假设A、B、C在内存中不同的单元

| Stack | Accumulator | Register (register-memory) | Register (load-store) |
|---|---|---|---|
| Push A | Load A | Load R1, A | Load R1,A |
| Push B | Add B | Add R1, B | Load R2,B |
| Add | Store C | Store C, R1 | Add R3,R1,R2 |
| Pop C |  |  | Store C R3 |

![](bbox=[0.12, 0.62, 0.85, 0.95])