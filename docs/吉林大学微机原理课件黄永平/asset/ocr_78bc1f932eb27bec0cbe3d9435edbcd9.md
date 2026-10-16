# 堆栈传参数
用出栈取参数例
子。
用CALL, RET

# 主程序

...

+   1. 子程序需要的参数入栈
+   MOV AX, 参数1
+   PUSH AX
+   MOV AX, 参数2
+   PUSH AX

+   2. CALL 子程序(段内调用)

断点CS:IP

...

...

# 结束

# 子程序

+   取参数:
+   POP DX ;断点IP保存到DX
+   POP AX ;取参数2
+   POP BX ;取参数1
+   PUSH DX ;断点放到栈顶

使用参数

# RET

初始
SS:SP

两参数入栈
SS:SP
参数2
参数1

CALL之后
SS:SP
IP
参数2
参数1

POP DX
SS:SP
IP
参数2
参数1
SS:SP

POP AX
POP BX
SS:SP
IP
参数2
参数1

PUSH DX
SS:SP
IP
参数2
IP