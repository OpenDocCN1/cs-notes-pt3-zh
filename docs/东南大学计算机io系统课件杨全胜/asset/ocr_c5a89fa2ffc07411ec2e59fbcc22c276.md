# 6.4 Programming the 82C55

# Control Word

+   Write only (A1A0=11)

| D7 | D6 | D5 | D4 | D3 | D2 | D1 | D0 |
|---|---|---|---|---|---|---|---|
| FLAG =1 | Group A Mode
00=Mode 0
01=Mode 1
1X=Mode 2 | Port A
0=output
1=input | Port C Upper
0=output
1=input | Group B Mode
0=Mode 0
1=Mode 1 | Port B
0=output
1=input | Port C Lower
0=output
1=input |

e.g. In one system, the Address of 82C55 is 60H~63H, Port A in mode 1, input, Port B in mode 0, output, Port C upper part as input, lower as output, please write the Control word.

```
MOV AL, 0B8H ; 10111000B
OUT 63H, AL
```