# 三、伪指令

HYPer

# 模块连接伪指令(PUBLIC,EXTRN)

# 1.PUBLIC全局符说明伪指令

```
PUBLIC 符号1 [, 符号2, ...]
```

功能：全局符号定义，其它模块可使用。

# 2.EXTRN外部符说明伪指令

```
EXTRN 符号1:类型 [, 符号2: 类型, ...]
```

功能：其它模块用PUBLIC定义的，本模块要引用的符号。

符号可以是：常量、变量、标号、过程名。

BYTE WORD
DWORD FWORD
QWORD TBYTE
ABS (用EQU定义的常量)
NEAR FAR(标号, 过程名)