# 程序设计语言（2）

汇编语言

```
MOV AX ,X
CMP AX ,Y
JL  S1
SUB AX ,15
JMP S2
S1: ADD AX ,15
S2: MOV Y ,AX
... ... ... ... ... ...
X DW ?
Y DW ?
```