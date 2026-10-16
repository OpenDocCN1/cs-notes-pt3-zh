# 计算序列: Jumps

|  | jXX Dest | 备注 |
|---|---|---|
| 取指 | icode:ifun ← M₁[PC]
valC ← M₈[PC+1]
valP ← PC+9 | 读指令字节
读目的地址
Fall through address |
| 译码 |  |  |
| 执行 | Cnd ← Cond(CC,ifun) | 是否选择分支 |
| 访问 |  |  |
| 写回 |  |  |
| 更新PC | PC ← Cnd ? valC : valP | 更新PC |

+   - 计算两个地址
+   - 根据条件码和分支条件作出选择