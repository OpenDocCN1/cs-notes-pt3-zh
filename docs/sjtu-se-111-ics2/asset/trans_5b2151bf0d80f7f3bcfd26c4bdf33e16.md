

## 前景与背景

- 如果最后一个参数是 "&" 字符
  - parseline 返回 1
  - 表示程序应在后台执行
  （shell 返回到循环顶部并等待下一个命令）
- 否则
  - parseline 返回 0
  - 表示程序应在前台运行
  （shell 等待其完成）

```c
if (!builtin_command(argv)) {
    if ((pid = Fork()) == 0) { /* execute in child */
        if (execve(argv[0], argv, environ) < 0) {
            printf("%s: Command not found.\n", argv[0]);
            exit(0);
        }
    }
}

/* parent waits for foreground job to terminate */
if (!bg) { /* foreground */
    int status;
    if (waitpid(pid, &status, 0) < 0)
        unix_error("waitfg: waitpid error");
}
else
    printf("%d %s", pid, cmdline);
}
return;
}
```

## 异常控制流 IV

## 大纲

- 信号
  - 信号术语
  - 发送信号
  - 接收信号
- 建议阅读 8.5.1~8.5.3

## 信号

- Unix 信号
  - 异常的更高层软件形式
  - 允许进程和内核中断其他进程

## kill 程序

- Kill 程序
  - 位于目录 `/bin/`
  - 向另一个进程发送任意信号

```
e.g. unix> kill -9 15213
```

- 向进程 15213 发送信号 9（SIGKILL）。

## 信号类型

- 信号是通知进程的消息
  - 系统中发生了某种类型的事件。
- 每种类型对应某种系统事件
  - 低级 **硬件** 异常
    - 由内核的异常处理程序处理，通常对用户进程不可见。
    - 信号提供了一种将此类异常的发生暴露给用户进程的机制。
  - 高级 **软件** 事件
    - 在内核中
    - 在其他用户进程中

## 硬件事件

- SIGFPE 信号（编号 8）
  - 如果进程尝试除以零，则内核向其发送 SIGFPE 信号
- SIGILL 信号（编号 4）
  - 如果进程执行非法指令，内核向其发送 SIGILL 信号。
- SIGSEGV 信号（编号 11）
  - 如果进程进行非法内存引用，内核向其发送 SIGSEGV 信号。

## 软件事件

- **SIGINT 信号（编号 2）**
  - 当进程在前台运行时
  - 如果你输入 ctrl-c
  - 则内核向该进程发送 SIGINT 信号
- **SIGKILL 信号（编号 9）**
  - 一个进程可以强制终止另一个进程
  - 通过向其发送 SIGKILL 信号
- **SIGCHLD 信号（编号 17）**
  - 当子进程终止或停止时，
  - 内核向父进程发送 SIGCHLD 信号。

## Linux 信号

```
> man signal
```

| 编号 | 名称 | 默认动作 | 对应事件 |
|---|---|---|---|
| 1 | SIGHUP | 终止 | 终端线路挂断 |
| 2 | SIGINT | 终止 | 来自键盘的中断 |
| 3 | SIGQUIT | 终止 | 来自键盘的退出 |
| 4 | SIGILL | 终止 | 非法指令 |
| 5 | SIGTRAP | 终止并转储核心 (1) | 跟踪陷阱 |
| 6 | SIGABRT | 终止并转储核心 (1) | 来自 abort 函数的终止信号 |
| 7 | SIGBUS | 终止 | 总线错误 |
| 8 | SIGFPE | 终止并转储核心 (1) | 浮点异常 |
| 9 | SIGKILL | 终止 (2) | Kill 程序 |
| 10 | SIGUSR1 | 终止 | 用户定义信号 1 |
| 11 | SIGSEGV | 终止并转储核心 (1) | 无效内存引用（段错误） |
| 12 | SIGUSR2 | 终止 | 用户定义信号 2 |
| 13 | SIGPIPE | 终止 | 向没有读者的管道写入 |
| 14 | SIGALRM | 终止 | 来自 alarm 函数的计时器信号 |
| 15 | SIGTERM | 终止 | 软件终止信号 |
| 16 | SIGSTKFLT | 终止 | 协处理器上的堆栈故障 |
| 17 | SIGCHLD | 忽略 | 一个子进程已停止或终止 |
| 18 | SIGCONT | 忽略 | 如果进程已停止则继续进程 |
| 19 | SIGSTOP | 直到下一个 SIGCONT 停止 (2) | 非终端的停止信号 |
| 20 | SIGTSTP | 直到下一个 SIGCONT 停止 | 来自终端的停止信号 |

