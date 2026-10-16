# 核心级线程

# 核心级线程和用户级线程区别，哪个快？

+   - ThreadCreate是系统调用，会进入内核，内核知道TCB

+   - gcc -o explorer explorer.c yield.c ...

+   - 内核级线程gcc -o explorer explorer.c...； ThreadCreate是系统调用； Yield()用户不可见，调度点由系统决定

进程 1

进程 2

用户

核心

线程 1

线程 n

硬件

线程IO, Schedule...

![](bbox=[0.22, 0.3, 0.7, 0.78])