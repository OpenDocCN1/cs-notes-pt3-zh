# 2.串比较指令

| 名称 | 格式 | 功能 | 状态标志 | 控制标志 |
| --- | --- | --- | O S Z A P C | D I T |
| 字节串比较指令 | CMPSB | 字节串比较 | O S Z A P C | 设置D |
| 字串比较指令 | CMPSW | 字串比较 | O S Z A P C | 设置D |
|  | REPE/REPZ | 当相等/为零重复 | 不影响 |  |
|  | REPN E/REPNZ | 当不相等/不为零重复 | 不影响 |  |

+   - D为方向标志（Direction Flag）：
+     D=1，串操作时地址自动减量，指令 STD； D=0，串操作时地址自动增量。指令 CLD
+   - REPE和REPZ是同一条指令的两种不同表示形式。
+   - REPN E和REPNZ是同一条指令的两种不同表示形式。