# 程序设计

```
DATA    SEGMENT
COUNT   DB      00H             ; 采样次数
NUMBER  DB      00H             ; 通道号
ADCBUF  DB      8 DUP(?)        ; 采样数据缓冲区
DATA    ENDS
ADCC    EQU     84H             ; A/D 控制口地址
ADCS    EQU     88H             ; A/D 状态口地址
CODE    SEGMENT
        ASSUME  CS:CODE, DS:DATA
START:  MOV     AX, DATA
        MOV     DS, AX
        MOV     BX, OFFSET ADCBUF   ; 设置 A/D 缓冲区
        MOV     CL, COUNT           ; 设置采样次数
        MOV     DL, NUMBER          ; 设置通道号
X3:     MOV     AL, DL
        OUT     ADDC, AL            ; 启动 ADC 0809 相应通道
```