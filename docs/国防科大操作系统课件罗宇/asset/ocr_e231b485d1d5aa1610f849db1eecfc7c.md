举例：（UNIX中两进程利用信号通讯）。
Process A
kill(1040, SIGUSR1); #向1040号进程发送一个SIGUSR1信号。

Process B
Signal(SIGUSR1,func);#当收到SIGUSR1信号时，就执行func()，如果SIGUSR1信号未到，则系统登记func函数，待其信号到时再调用执行。