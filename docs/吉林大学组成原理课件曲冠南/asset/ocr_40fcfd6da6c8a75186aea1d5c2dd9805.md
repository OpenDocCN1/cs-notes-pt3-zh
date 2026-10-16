# (1) 相对寻址举例

```
LDA  # 0
LDX  # 0
M    ADD  X, D
M+1  INX
M+2  CPX  # N
M+3  BNE  M
DIV  # N
STA  ANS
```

* 相对寻址特征

M 随程序所在存储空间的位置不同而不同

而指令 BNE *-3 与指令 ADD X, D 相对位移量不变

指令 BNE *-3 操作数的有效地址为

```
EA = ( M+3 ) - 3 = M
```