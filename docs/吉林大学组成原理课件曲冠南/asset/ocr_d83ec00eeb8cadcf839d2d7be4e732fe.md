# 九、微程序设计举例

# 1. 写出对应机器指令的微操作及节拍安排

假设 CPU 结构与组合逻辑相同

# （1）取指阶段微操作分析

3 条微指令

| 节拍 | 微操作 | 说明 |
|---|---|---|
| $T_0$ | $PC \rightarrow MAR$ | $1 \rightarrow R$ |
| $T_1$ | $M(MAR) \rightarrow MDR$ | $(PC)+1 \rightarrow PC$ |
| $T_2$ | $MDR \rightarrow IR$ | $OP(IR) \rightarrow$ 微地址形成部件 |

若需考虑如何安排这条微指令？

则取指操作需 3 条微指令

$Ad(CMAR) \rightarrow CMAR$

$OP(IR) \rightarrow$ 微地址形成部件 $\rightarrow CMAR$