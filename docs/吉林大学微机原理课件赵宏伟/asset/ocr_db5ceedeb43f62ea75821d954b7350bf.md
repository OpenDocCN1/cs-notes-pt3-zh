```
```
BAD_MODE: MOV AX, DATA
MOV ES, AX
MOV AH, 3 ; 读光标位置功能调用
MOV BH, 0 ; 0 页
INT 10H ; DX 中有光标位置
MOV DL, 0 ; 选 0 列
MOV AX, 1300H ; 写字符串
MOV BH, 0 ; 0 页
MOV BL, 3 ; 颜色号为 3
LEA BP, MSG ; 字节的偏移地址
MOV CX, N ; 字符串长度
INT 10H
MOV AH, 4CH
INT 21H
MAIN ENDP
CODE ENDS
END START
```
```