# 【例4.22】

某一源程序需要多次将AX, BX, CX, DX寄存器的内容压入堆栈，则可定义如下宏指令。

```
PUSHR      MACRO
           IRP  REG,  <AX, BX, CX, DX>
           PUSH REG
           ENDM
           ENDM
```

调用上述宏定义后，将展开成下列语句：

```
+ PUSH  AX
+ PUSH  BX
```