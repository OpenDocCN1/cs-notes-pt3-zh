```
START:      MOV AX, DATA
            MOV DS, AX
            MOV CX, N
            DEC CX
LOOP1:      MOV DX, CX
            MOV BX, 0
LOOP2:      MOV AX, BUF[BX]
            CMP AX, BUF[BX+2]
            JGE L
            XCHG AX, BUF[BX+2]
            MOV BUF[BX], AX
```