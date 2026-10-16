# Y86-64 程序结构 1

```
init:		# Initialization
...
    call Main
    halt
.align 8		# Program data
array:
...
Main:		# Main function
...
    call len
...
len:		# Length function
...
.pos 0x100	# Placement of stack
Stack:
```

+   - 程序从地址0处开始
+   - 一定要建立栈
+     - 位于哪里
+     - 指针的值
+     - 确保不要覆盖代码区域
+   - 一定要初始化数据