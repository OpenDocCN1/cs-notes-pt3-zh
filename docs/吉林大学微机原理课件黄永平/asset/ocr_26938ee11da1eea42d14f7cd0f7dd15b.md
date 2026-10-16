# 几点注意（数据传送等宽原则）

# HYPer

# 4. 数据传送等宽原则

数据传送等宽原则，也就是类型要正确

! 取X变量值(DB类型时)
X DB 20h, 30h, 40h, 50h

![](bbox=[0.48, 0.38, 0.82, 0.52])

```
MOV AL, X      ;正确
MOV AL, [X]     ;正确
二者等效
```

```
MOV AX, X       ;! 错误
MOV AX, [X]     ;! 错误
```

```
MOV AX, WORD PTR X      ;正确
MOV AX, WORD PTR [X]    ;正确
```