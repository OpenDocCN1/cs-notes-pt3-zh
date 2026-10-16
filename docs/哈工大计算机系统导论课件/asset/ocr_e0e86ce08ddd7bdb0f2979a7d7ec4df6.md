# 设置信号处理程序

+   - 可以使用 signal函数修改和信号signum相关联的默认行为:
+     - handler_t *signal(int signum, handler_t *handler)

+   - handler的不同取值:
+     - SIG_IGN: 忽略类型为signum的信号
+     - SIG_DFL: 类型为 signum的信号行为恢复为默认行为
+     - 否则，handler 就是用户定义的函数的地址，这个函数称为信号处理程序
+       - 只要进程接收到类型为 signum 的信号就会调用信号处理程序
+       - 将处理程序的地址传递到signal函数从而改变默认行为，这叫做设置信号处理程序
+       - 调用信号处理程序称为捕获信号
+       - 执行信号处理程序称为处理信号
+       - 当处理程序执行return时，控制会传递到控制流中被信号接收所中断的指令处