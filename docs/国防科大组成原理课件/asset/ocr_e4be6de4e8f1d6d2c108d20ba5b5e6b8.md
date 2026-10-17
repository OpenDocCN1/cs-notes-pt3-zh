# 系统调用和陷入

+   - 软件故意产生的异常
+   - 系统调用：操作系统为用户态程序访问核心态资源准备的接口
+   - 陷入：软件预设的断点，如MIPS的TRAP指令、整数除零检查

```
li      v0, ID
syscall

bnez    v0, 1f
div     zero, v1, v0
break   0x7
1:

teq     v0, $0, 0x7
div     zero, v1, v0
```