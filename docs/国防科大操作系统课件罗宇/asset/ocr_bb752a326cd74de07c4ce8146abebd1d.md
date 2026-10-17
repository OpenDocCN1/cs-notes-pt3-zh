# 系统调用

+   系统调用表在哪里？

在/usr/src/linux-2.4.22/arch kernel/entry.S中
打开这个文件，翻到末尾

```
ENTRY(sys_call_table)
.long SYMBOL_NAME(sys_ni_syscall)
/* 0 - old "setup()" system call*/
.long SYMBOL_NAME(sys_exit)
.long SYMBOL_NAME(sys_fork)
.long SYMBOL_NAME(sys_read)
.long SYMBOL_NAME(sys_write)
open)
/* 5 */
```

表中标有sys_ni_syscall的，是指这一项没有被使用。

按照Linux的习惯，给系统调用名字前面加“sys_”，作为系统调用的处理函数名。

![](bbox=[0.72, 0.55, 0.97, 0.97])

![](bbox=[0.83, 0.01, 0.99, 0.33])