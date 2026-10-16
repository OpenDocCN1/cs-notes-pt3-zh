# 2.6.7 Procedure Instructions

+   - Passing Parameters
+     - Passing Parameters in 16-bit program
+       - by register

Define a procedure “DECIBIN” to input a decimal number from keyboard, the number return by BX.

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