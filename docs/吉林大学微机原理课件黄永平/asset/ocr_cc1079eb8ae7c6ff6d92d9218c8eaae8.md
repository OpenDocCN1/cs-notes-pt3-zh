# 四、操作数字段

HYPer

（6）属性运算符：

2) 变量/标号 EQU THIS 类型

对变量：指定变量类型为BYTE, WORD,DWORD, FWORD,QWORD,TBYTE.

对标号：指定标号类型为 NEAR ， FAR.

为声明一个变量/标号，但不分配存储区。

```
DATA1 EQU THIS BYTE
```

```
DATA2 DW 1234H,5678H
```

```
MOV AX, DATA2    ;1234H
```

```
MOV BL, DATA1    ;34H
```

```
MOV BH, DATA1+1  ;12H
```

```
AA1 EQU THIS FAR
```

```
AA2: MOV AX,100H
```

DATA1 DATA2地址相同，类型不同

AA1 AA2地址相同，类型不同