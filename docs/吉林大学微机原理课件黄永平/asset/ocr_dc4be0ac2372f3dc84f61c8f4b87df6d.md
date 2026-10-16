# 2) 无符号数大小的比较转移(A-B)

JX disp8
; X 为标志条件, 可能是两个条件的组合，A，B，E，N
IP ← IP + disp8 , disp8 = -128~127

根据组合条件标志的设置情况转移 —— 主要用来比较两个数的大小

| 指令 | 功能 | 转移条件 |
|---|---|---|
| JA / JNBE disp8 | (>) 高于/不低于也不等于则转移 | CVZ=0 |
| JAE / JNB / JNC disp8 | (≥) 高于或等于/不低于/无借位则转移 | C=0 |
| JB / JNAE / JC disp8 | (<) 低于/不高于也不等于/有借位则转移 | C=1 |
| JBE / JNA disp8 | (≤) 低于或等于/不高于则转移 | CVZ=1 |

A—Above, B—Below, E—Equal, N--Not