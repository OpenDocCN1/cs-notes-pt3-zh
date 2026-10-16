# 2.6.6 String Instructions

# String Data Transfer Instructions

# STOS Instruction example

Clear the buff

```
```asm
.DATA
BUFF DB 1000 DUP(?)  ; define the buffer
.CODE
        ......
CLD                    ; DF=0
LEA  DI, BUFF          ; address of buff-->DI
MOV  CX, 1000          ; the number of repetitions
MOV  AL, 0             ; 0-->AL
REP  STO SB            ; store 0 to clear
```
```