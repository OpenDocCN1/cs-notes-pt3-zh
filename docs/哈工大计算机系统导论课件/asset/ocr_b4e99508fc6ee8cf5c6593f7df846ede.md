# Intel Haswell CPU的能力

+   - 多条指令可以并行执行
+     - 2 load（加载）
+     - 1 store（存储）
+     - 4 integer（整型）
+     - 2 FP multiply（浮点乘）
+     - 1 FP add / divide（浮点加/除）

+   - 有些指令花费多于一个周期，但是仍可以流水化

| 指令 | 延迟 | 周期数（周期s/Issue） |
|---|---|---|
| Load / Store | 4 | 1 |
| Integer Multiply | 3 | 1 |
| Integer Divide | 3—30 | 3—30 |
| Double/Single FP Multiply | 5 | 1 |
| Double/Single FP Add | 3 | 1 |
| Double/Single FP Divide | 10—15 | 6—11 |