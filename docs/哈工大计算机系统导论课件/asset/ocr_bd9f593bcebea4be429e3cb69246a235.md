# 数组移位：右移1位(intel 格式)

```
.data
  arraysize = 10
  array dword arraysize dup(76543210h)
.code
main PROC
  mov esi, (arraysize-1)*(type array)
  mov ecx, arraysize
  clc
  lahf
```

```
L:
  sahf
  rcr array[esi],1
  lahf
  sub esi,type array
  loop L
  exit
main ENDP
END main
```

将上述intel格式代码改写成ATT格式！