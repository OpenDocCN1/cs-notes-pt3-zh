

## 2.6.7 程序指令

### 程序定义

```
LABEL PROC [attributes]
...; procedure body
RET
...; procedure body
LABEL ENDP
```

- 程序体始终跟随一个 .CODE 指令。
- 程序体由两个指令 PROC 和 ENDP 括起来
- 标签给出程序的名称。
- 属性：near 或 far
- 至少有一个 RET 指令

### 程序定义

**定义一个程序向屏幕输出 CRLF。（16 位程序使用）**

```
CRLF  PROC NEAR    ; output Carriage Return and Line Feed
      PUSH AX
      PUSH DX
      MOV  DL, 0DH    ; Carriage Return
      MOV  AH, 2
      INT  21H       ; output char in DL
      MOV  DL, 0AH    ; Line Feed
      MOV  AH, 2
      INT  21H       ; output char in DL
      POP  DX
      POP  AX
      RET
CRLF  ENDP
```

### 参数传递

### 16 位程序中的参数传递

通过寄存器

定义一个过程 “PINT” 输出 AX 中的十进制数，转换缓冲区的偏移量在 DI 中。

```
PINT    PROC    NEAR
    PUSH    DX
    PUSH    DI
    PUSH    CX
    MOV     CX, 5
CLEAR_BUF:MOV BYTE PTR[DI], ' '
    INC     DI
    LOOP    CLEAR_BUF
    MOV     BYTE PTR[DI], '$'
    DEC     DI
    MOV     CX, 10
CHANGE: MOV DX, 0
    DIV     CX
```

```
ADD     DL, 30H
MOV     BYTE PTR[DI], DL
DEC     DI
CMP     AX, 0
JNZ     CHANGE
INC     DI
MOV     DX, DI
MOV     AH, 9
INT     21H
POP     CX
POP     DI
POP     DX
RET
PINT    ENDP
```

- 参数传递
  - 16 位程序中的参数传递
    - 通过寄存器

定义一个过程 “DECIBIN” 从键盘输入一个十进制数，数字通过 BX 返回。

```
DECIBIN PROC NEAR
    PUSH  AX
    PUSH  CX
    MOV   BX, 0 ; initial
NEWCHAR:MOV AH, 1
    INT   21H ; ASCII in AL
    SUB   AL, 30H
    JL    EXIT   ; < 0
    CMP   AL, 9
    JG    EXIT   ; > 9
    CBW
```

```
XCHG  AX, BX
MOV   CX, 10
MUL   CX   ; old value *10
XCHG  AX, BX
ADD   BX, AX ;add new value
JMP   NEWCHAR
EXIT: POP   CX
      POP   AX
      RET
DECIBIN ENDP
```

### 参数传递

- 16 位程序中的参数传递
  - 通过堆栈

**定义一个过程 “PROSUM” 计算 WORD 数组的和。元素数量在 COUNT 中，结果将放在 SUM 中。**

```asm
.DATA
    ARRAY  WORD 10 DUP(?)
    COUNT  WORD 10
    SUM    WORD ?
```
**主程序：**

```
LEA BX,ARRAY    ; parameter in stack
PUSH BX
LEA BX,COUNT
PUSH BX
LEA BX,SUM
PUSH BX
CALL PROSUM
......

PROSUM PROC NEAR
    PUSH BP
    MOV BP,SP
    PUSH AX
    PUSH CX
    PUSH SI
    PUSH DI
```

![](img/d7c975450dfbe59120092c2721be78c6_283_0.png)

3 个参数压入堆栈，每个使用两个字节

```
MOV SI, [BP+8] ; get parameter
MOV DI, [BP+6]
MOV CX, [DI]
MOV DI, [BP+4]
MOV AX, 0
ADDT: ADD AX, [SI]
      ADD SI, 2
      LOOP ADDT
MOV [DI], AX ; save sum
POP DI
POP SI
POP CX
POP AX
POP BP
RET 6 ; adjust stack
```

![](img/d7c975450dfbe59120092c2721be78c6_284_0.png)

### 参数传递

### 16 位程序中的参数传递

### 示例

**输入** 数组中的 10 个数字，然后计算其元素的和。

```asm
.8086
.MODEL SMALL
.DATA
    ARRAY  WORD 10 DUP(?)
    COUNT  WORD 10
    SUM    WORD ?
    STRING BYTE 6 DUP(?)
.STACK 1024
```

```
.8086
.MODEL SMALL
.DATA
    ARRAY  WORD 10 DUP(?)
    COUNT  WORD 10
    SUM    WORD ?
    STRING BYTE 6 DUP(?)
.STACK 1024
.CODE
START:
    MOV   AX,@DATA
    MOV   DS,AX
    LEA   DI,ARRAY
    MOV   CX,10
LP: CALL  DECIBIN
    CALL  CRLF
    MOV   [DI],BX
```

```
ADD   DI,2
LOOP  LP ;input 10 numbers
LEA   BX,ARRAY
PUSH  BX
LEA   BX,COUNT
PUSH  BX
LEA   BX,SUM
PUSH  BX
CALL  PROSUM
MOV   AX,SUM
LEA   DI,STRING
CALL  PINT
CALL  CRLF
MOV   AX,4C00H
INT   21H
......   ; subroutine
END START
```

