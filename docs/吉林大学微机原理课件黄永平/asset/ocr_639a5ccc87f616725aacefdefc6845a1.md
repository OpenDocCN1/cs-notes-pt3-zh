```
BUFB          DB 81 DUP (0)
DATA          ENDS
CODE          SEGMENT
              ASSUME DS: DATA, SS: STACK, CS: CODE
START:        MOV   AX, DATA
              MOV   DS, AX
              RETURN      ; 输出回车换行
              PRINT INFO1 ; 输出字符变量INFO1 代表的字符
字符串
              INPUT BUFA  ; 键盘输入字符中到缓冲区；
              LEA   SI, BUFA+1
              MOV   CH, 0
              MOV   CL, [SI]
              ADD   SI, CX
              LEA   DI, BUFB
```