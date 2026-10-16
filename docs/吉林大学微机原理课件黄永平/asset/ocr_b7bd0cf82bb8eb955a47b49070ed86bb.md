```
STACK      ENDS
CODE       SEGMENT
           ASSUME DS: DATA, CS: CODE, SS: STACK
BEGIN:     MOV   AX, DATA
           MOV   DS, AX
           DOSYS 9, MSG
           DOSYS 10 , BUF
           DOSYS 4CH
CODE ENDS
END  START
```