```
ASSUME DS: DATA, SS: STACK, CS: CODE
BEGIN:
    MOV AX, DATA
    MOV DS , AX
    LEA BX, TAB
    MOV AL, NO
    DEC AL
    XLATB            ; al←[bx+al]
    MOV ENGLISH, AL
    MOV AH, 4CH
    INT  21H
CODE  ENDS
    END BEGIN
```