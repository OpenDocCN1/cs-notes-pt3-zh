# 例6-1：在数据段DS中有一字符串，试将其每一个字加一后送入附加段ES中。

```
LEA SI, souce
LEA DI, dest
MOV CX, 20
CLD
again: LODSW
INC AX
MOV ES:[DI], AX
INC DI
INC DI
DEC CX
JNZ again
HLT
```

AL ← DS:[SI]
SI ← SI +1

Lods 指令一般不与 Rep指令配合使用

![](bbox=[0.75, 0.24, 0.95, 0.85])