# 6.5 Application

```
```asm
.DATA
BUFF    BYTE 'HELLO,WORLD!', 13, 10, '$'
PORTA   EQU 60H
PORTB   EQU 61H
PORTC   EQU 62H
PORTCN  EQU 63H

.CODE
START:  MOV     AX, @DATA
        MOV     DS, AX
        MOV     SI, OFFSET BUFF
```
```