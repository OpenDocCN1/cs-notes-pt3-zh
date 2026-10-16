```
START:    MOV  AX, DATA
          MOV  DS, AX
          MOV  AX, BUF
          MOV  CL, 0  ; 计数器为0
COPA:     AND  AX, AX
          JE   EXIT   ; (AX) =0, 结束循环
          SHL  AX, 1  ; AX 左移一位
          JNC  LOPA
          INC  CL      ; 产生进位， (CL) +1→CL
          JMP  LOPA
EXIT:     MOV  COUNT, CL
          MOV  AH, 4CH
          INT  21H
CODE      ENDS
          END  START
```