# Y86-64 程序结构 2

```
init:
    # Set up stack pointer
    irmovq Stack, %rsp
    # Execute main program
    call Main
    # Terminate
    halt
# Array of 4 elements + terminating 0
.align 8
Array:
    .quad 0x000d000d000d000d
    .quad 0x00c000c000c000c0
    .quad 0x0b000b000b000b00
    .quad 0xa000a000a000a000
    .quad 0
```

+   - 程序从地址0处开始
+   - 一定要建立栈
+     - 位于哪里
+     - 指针的值
+     - 确保不要覆盖代码区域
+   - 一定要初始化数据
+   - 可以用符号化名字