# 计算序列

| | | OPq rA, rB |
|---|---|---|
| 取指 | icode,ifun | icode:ifun ← M1[PC] |
|  | rA,rB | rA:rB ← M1[PC+1] |
|  | valC |  |
|  | valP | valP ← PC+2 |
| 译码 | valA, srcA | valA ← R[rA] |
|  | valB, srcB | valB ← R[rB] |
| 执行 | valE | valE ← valB OP valA |
|  | Cond code | Set CC |
| 访存 | valM |  |
| 写回 | dstE | R[rB] ← valE |
|  | dstM |  |
| 更新PC | PC | PC ← valP |

读指令字节
读寄存器字节
[读常数字]
计算下一条PC
读操作数A
读操作数B
执行ALU的操作
设置条件码寄存器
[读写内存]
ALU的运算结果写回
[内存结果写回]
更新PC

+   - 所有的指令有相同的格式
+   - 每一步计算的内容有区别