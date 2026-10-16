# 程序控制传送方式——查询输入传送

![](bbox=[0.02, 0.22, 0.78, 0.92])

```
next:IN AL, 0E2h
TEST AL,01h
JZ next
IN AL, 0E0h
...
```