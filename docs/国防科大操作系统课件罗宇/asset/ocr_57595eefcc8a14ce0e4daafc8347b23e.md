+   - TASK_STOPPED：进程处于暂停状态，主要用于调试目的。如正在运行的进程收到SIGSTOP信号将进入TASK_STOPPED状态。
+   - TASK_ZOMBIE：表示进程已经结束运行并释放了大部分占用的资源，但task_struct结构还未被释放。