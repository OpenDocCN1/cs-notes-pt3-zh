# 3)段间直接调用指令(远过程)

```
CALL FAR PTR addr32
```

; SP ← SP − 2, Stack ← CS (CS入栈)

SP ← SP − 2 , Stack ← IP (IP入栈)

IP ← addr32偏移地址

CS← addr32段地址

![](bbox=[0.62, 0.42, 0.92, 0.62])

CALL F_PROC; F_PROC为远过程名

CALL 2000h:1000h

+   • 与段间直接转移 JMP FAR PTR addr32的区别？