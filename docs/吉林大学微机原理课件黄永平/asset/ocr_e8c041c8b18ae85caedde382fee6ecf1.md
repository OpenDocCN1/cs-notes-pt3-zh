# 方法2

C
AX

C
DX

```
org
MOV DX,1234H
MOV AX,5678H
MOV CL,4
loop1:SHL AX,1
RCL DX,1
DEC CL
JNZ loop1
ret
```

循环移位指令的作用：
循环移位指令可以改变操作数
中所有位的位置