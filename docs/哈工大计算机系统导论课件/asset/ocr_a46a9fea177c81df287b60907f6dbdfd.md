# Haswell 架构的Intel CPU

+   - 8 个功能单元—P359

# 可并行执行多条指令

+   - 2个加载，带地址计算
+   - 1个存储，带地址计算
+   - 4个整数运算
+   - 2个浮点乘法运算
+   - 1个浮点加法
+   - 1个浮点除法

# 某些指令 > 1 周期,但能够被流水

| 指令 | 延迟Latency | 周期/发射 |
|---|---|---|
| Load / Store | 4 | 1 |
| Integer 乘法 | 3 | 1 |
| Integer/Long 除法 | 3-30 | 3-30 |
| Single/Double FP 乘法 | 5 | 1 |
| Single/Double FP 加法 | 3 | 1 |
| Single/Double FP 除法 | 3-15 | 3-15 |