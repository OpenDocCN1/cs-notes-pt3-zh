# *1) 输入字符(AH = 1, 7)

```
MOV AH, 1
INT 21h
```

AH=7 无回显

输出： AL = 键盘上输入的字符的ASCII码

; 等待敲击键盘,AL中得到ASCII码

# *2) 显示字符(AH = 2)

输入： DL = 要显示字符的ASCII码

```
MOV AH, 2
INT 21h
```

; 显示DL中的ASCII码