# 7.8 加锁协议—Lock Protocol

封锁法是最基本的并发控制方法之一，它可以有多种实现方式。

X locks: Only one type of lock, for both read and write

相容矩阵：NL—no lock　　X—X lock
Y—相容　　　 N—不相容

| 已有\\待加 | NL | X |
|---|---|---|
| NL | Y | Y |
| X | Y | N |

![](bbox=[0.522, 0.704, 0.634, 0.957])

![](bbox=[0.738, 0.674, 0.846, 0.957])