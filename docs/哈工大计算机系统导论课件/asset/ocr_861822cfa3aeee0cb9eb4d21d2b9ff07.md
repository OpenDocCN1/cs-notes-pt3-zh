# 32位有符号除法

```
.data
Val: .int -5000
.text
movl Val, %eax
cdq
mov $256, %ebx
idiv %ebx
```

+   1. 必□将被除数的符号位从EAX扩展到EDX
+   2. 商被放入EAX中，余数被放入EDX中

EAX = 0xFFFFFFED = -19
EDX = 0xFFFFFF78 = -136