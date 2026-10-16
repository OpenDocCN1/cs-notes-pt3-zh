# 加锁原则：

+   Locks are requested from root to leaves and released from leaves to root.

+   例：

加锁顺序

|  | record | file | DB |
|---|---|---|---|
| (1) | S | IS | IS |
| (2) | X | IX | IX |
| (3) | All read and some write | SIX | IX, IS |
|  | 对要写的record加X锁 |  | 以强代弱 |

DB
File
Record
Field