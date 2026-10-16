# 例3-1：字比较。

```
LEA SI, souce
LEA DI, dest
MOV CX, 25
CLD
Again: CMPSW
JNZ Found
DEC CX
JNZ Again
MOV AX, 0
JMP exit
Found : DEC SI
DEC SI
MOV AX,SI
Exit: HLT
```

![](bbox=[0.28, 0.16, 0.75, 0.52])

![](bbox=[0.75, 0.13, 0.92, 0.88])