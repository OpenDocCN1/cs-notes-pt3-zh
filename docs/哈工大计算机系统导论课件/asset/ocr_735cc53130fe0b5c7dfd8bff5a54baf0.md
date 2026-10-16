# 计算序列: Cond. Move

| | cmovXX rA, rB | |
|---|---|---|
| 取指 | icode:ifun ← M₁[PC]
rA:rB ← M₁[PC+1]
valP ← PC+2 | 读指令字节
读寄存器字节
计算下一条PC |
| 译码 | valA ← R[rA]
valB ← 0 | 读操作数A |
| 执行 | valE ← valB + valA
If ! Cond(CC,ifun) rB ← 0xF | 利用ALU传递数据A
(阻止寄存器更新) |
| 访存 |  |  |
| 写回 | R[rB] ← valE | 结果写回 |
| 更新PC | PC ← valP | 更新PC |

+   - 读rA寄存器并通过ALU传递数据
+   - 通过将端口值设为0xF来取消数据写入寄存器
+     - 如果条件码和传送条件表明无需传送数据