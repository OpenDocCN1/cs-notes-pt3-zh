# 系统调用的例子: 打开文件

+   用户调用函数: open(filename, options)
+   调用__open函数，该函数使用系统调用指令syscall

```
00000000000e5d70 <__open>:
...
e5d79: b8 02 00 00 00    mov $0x2,%eax # open is syscall #2
e5d7e: 0f 05            syscall      # Return value in %rax
e5d80: 48 3d 01 f0 ff ff cmp $0xfffffffffffff001,%rax
...
e5dfa: c3               retq
```

![](bbox=[0.04, 0.68, 0.58, 0.93])

+   %rax 包含系统调用号
+   其他参数(最多6个)依次在 %rdi, %rsi, %rdx, %r10, %r8, %r9
+   返回值在 %rax
+   负数返回值表明发生了错误，对应于负的errno