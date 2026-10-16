# Counter 2, Speaker Tone

; function: issued 896Hz sound

; parameter: CX= time interval

; return: none

```
BEEP PROC FAR
    IN      AL, 61H;  read 8255 PB port
    MOV     AH, AL
    PUSH    AX
    MOV     AL, 10110110B
    OUT     43H, AL
    MOV     AX, 0533H;  =1.1931816MHz/896Hz
    OUT     42H, AL
    MOV     AL, AH
    OUT     42H, AL
    POP     AX
```