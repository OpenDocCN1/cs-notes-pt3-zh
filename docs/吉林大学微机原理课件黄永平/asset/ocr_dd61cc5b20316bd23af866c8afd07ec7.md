# 例1： 将数据段中起始地址为Souce的100个字节的数据传送到附加段的Dest指向的单元中。

```
COUNT EQU 5
org 100h
LEA SI,source  ;与MOV SI,offset source一样
LEA DI,dest    ;与MOV DI,offset dest一样
MOV CX,COUNT
CLD
Again:
MOVSB
DEC CX
JNZ Again
ret
source db 65h,23h,02h,00h,24h
dest db 20 dup(?)
```

增址传送

[SI] → [DI]
SI+1 → SI
DI+1 → DI

![](bbox=[0.68, 0.15, 0.96, 0.95])