# MUL指令

```
mov $0x5,%al
mov $0x20,%bl
mul %bl
```

+   > 被乘数是AL，乘积被放入AX中
+   > 根据乘积中□半部分是否
+   为0，设置或清除CF位和
+   OF位
+   > 处理无符号数，只□关心
+   CF标志位

AX= 0x00A0

CF = 0、OF=0