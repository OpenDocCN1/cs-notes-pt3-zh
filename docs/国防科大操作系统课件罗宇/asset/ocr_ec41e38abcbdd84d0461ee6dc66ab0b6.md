# 实验二 知识要点回顾

+   - 我使用空闲的系统调用号250，添加了一个系统调用my_syscall()，当一个用户态程序调用my_syscall()的时候，简要说明一下在计算机内部的执行流程。

+   - 我在系统调用my_syscall()的处理程序里面写了这样一行：
+     printk("Hello, now we are in the kernel\n"
+     这里为什么用printk，而不是printf？