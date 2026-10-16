2F365
+ 5E024
--------
8D389
→
1 F365
+ E024
--------
D389
2 1
0002
+ 0005
--------
0008

```
MOV AX, First
ADD AX, Second
MOV Third, AX
MOV AX, First+2
ADC AX, Second+2
MOV Third+2, AX
```

|  | |
|---|---| 
| 65 | First |
| F3 | |
| 02 | |
| 00 | |
| 24 | Second |
| E0 | |
| 05 | |
| 00 | |
| 89 | Third |
| D3 | |
| 08 | |
| 00 | |