# 例7：在数据段DS中有一字符串，试将其每一个字符加一后送入附加段ES中。

```
LEA  SI, souce
LEA  DI, dest
MOV  CX, 30
CLD
again: LODSB
INC  AL
STOSB
DEC  CX
JNZ  again
HLT
```

AL ← DS:[SI]
SI ← SI +1

ES:[DI] ← AL
DI ← DI +1

![](bbox=[0.75, 0.2, 0.95, 0.82])