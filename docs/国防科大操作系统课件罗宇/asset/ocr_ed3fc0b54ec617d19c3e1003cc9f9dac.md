系统在初始化设置了0x80号异常的处理函数为sys_call()，该函数执行下面一条语句：

```
call *SYMBOL_NAME(sys_call_table)(,%eax,4)
```

sys_call_table为系统调用表，该表保存的是各个系统调用的入口地址，下面列出了系统调用表的最前面三项：

```
ENTRY(sys_call_table)
.long SYMBOL_NAME(sys_ni_syscall)/*第0号 */
.long SYMBOL_NAME(sys_exit)
.long SYMBOL_NAME(sys_fork)
```

从而fork()函数对应的系统调用为sys_fork()，该函数又调用do_fork()完成具体的工作