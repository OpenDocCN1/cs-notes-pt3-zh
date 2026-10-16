# 计算序列: call

|  | call Dest |  |
|---|---|---|
| 取指 | icode:ifun ← M₁[PC]
valC ← M₈[PC+1]
valP ← PC+9 | 读指令字节
读目的地址
计算返回指针 |
| 译码 | valB ← R[%rsp] | 读栈指针 |
| 执行 | valE ← valB + -8 | 栈指针减8 |
| 访存 | M₈[valE] ← valP | 返回值进栈 |
| 写回 | R[%rsp] ← valE | 更新栈指针 |
| PC更新 | PC ← valC | PC指向目的地址 |

+   - 利用ALU减少栈指针
+   - 存储增加后的PC