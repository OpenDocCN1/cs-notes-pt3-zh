# 3.4 自下而上分析

> $E \rightarrow E + E \mid E * E \mid (E) \mid id$

| 栈 | 输入 | 动作 |
|---|---|---|
| $ | id₁ * id₂ + id₃$ | 移进 |
| $ id₁ | * id₂ + id₃$ | 按 E → id 归约 |
| $E | * id₂ + id₃$ | 移进 |
| $E* | id₂ + id₃$ |  |