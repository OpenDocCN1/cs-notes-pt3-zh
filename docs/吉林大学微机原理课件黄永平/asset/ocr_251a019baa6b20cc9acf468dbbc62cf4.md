# 例5-2：初始化内存，使其内容全部位0。与 Rep 指令配合使用。

```
LEA DI, dest
MOV AL, 0
MOV CX, 30
CLD
REP STOSB
HLT
```

![](bbox=[0.72, 0.22, 0.88, 0.88])