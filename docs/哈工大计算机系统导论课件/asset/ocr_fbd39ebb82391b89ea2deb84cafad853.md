# 错误的返回示例

```
# demo-ret
0x033: ret
0x034: irmovq $1,%rax # Oops!
0x03e: irmovq $2,%rcx # Oops!
0x048: irmovq $3,%rdx # Oops!
0x052: irmovq $5,%rsi # Return
```

在ret之后，错误地执行了3条指令

![](bbox=[0.45, 0.2, 0.92, 0.98])