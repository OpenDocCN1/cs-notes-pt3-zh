# 例3：有一组无符号数，与50比较，大于50 的存入另一存储区，小于或等于50的放弃。

```
LEA SI, array1
LEA DI, array2
MOV CX, n
Again: MOV AL,[SI]
INC SI
CMP AL, 50
JBE next
MOV [DI], AL
INC DI
next: DEC CX
JNZ again
Hlt
```

array1

05
A2
00
10
85

array2

A2
85

![](bbox=[0.38, 0.48, 0.82, 0.82])