
# 两个连续的fork

```c
void fork2()
{
    printf("L0\n");
    fork();
    printf("L1\n");
    fork();
    printf("Bye\n");
}
```

![](img/7ab811dea080313a753fa0ae68528fa9_1368_0.png)

# 可能的输出:

- L0
- L1
- Bye
- Bye
- L1
- Bye
- Bye

# 不可能的输出:

- L0
- Bye
- L1
- Bye
- L1
- Bye
- Bye

# 父进程中的嵌套fork调用

```
forks.c

void fork4()
{
    printf("L0\n");
    if (fork() != 0) {
        printf("L1\n");
        if (fork() != 0) {
            printf("L2\n");
        }
    }
    printf("Bye\n");
}
```

可能的输出：
L0
L1
Bye
Bye
L2
Bye

不可能的输出：
L0
Bye
L1
Bye
Bye
L2

![](img/7ab811dea080313a753fa0ae68528fa9_1369_0.png)

# 练习

```
int main()
{
    int x = 1;

    if(Fork() == 0);
        printf("p1: x=%d\n", ++x);
    printf("p2: x=%d\n", --x);
    exit(0);
}
```

# 进程控制 ——
回收子进程(Reaping Child Processes)

- **想法**
  - 当进程终止时，它仍然消耗系统资源
    - Examples: Exit status, various OS tables(占用内存)
  - 称为“僵尸zombie”进程
    - 活着的尸体，半生半死

- **回收 (Reaping)**
  - 父进程执行回收(using wait or waitpid)
  - 父进程收到子进程的退出状态
  - 内核删掉僵死子进程

# 进程控制——
回收子进程(Reaping Child Processes)

- 父进程不回收子进程的后果：
  - 如果父进程没有回收它的僵死子进程就终止了，内核安排init进程去回收它们(init进程PID为1，系统启动时创建，不会终止，是所有进程的祖先)
  - 长时间运行的进程应当主动回收它们的僵死子进程
    - e.g., shells and servers

# 僵死进程

```
void fork7() {
    if (fork() == 0) {        /* Child */
        printf("Terminating Child, PID = %d\n", getpid());
        exit(0);
    } else {
        printf("Running Parent, PID = %d\n", getpid());
        while (1)            ; /* Infinite loop */
    }
}
forks.c
```

```
linux> ./forks7 &
[1] 6639
Running Parent, PID = 6639
Terminating Child, PID = 6640
linux> ps
  PID TTY        TIME CMD
6585 ttyp9    00:00:00 tcsh
6639 ttyp9    00:00:03 forks
6640 ttyp9    00:00:00 forks <defunct>
6641 ttyp9    00:00:00 ps
linux> kill 6639
[1]   Terminated
linux> ps
  PID TTY        TIME CMD
6585 ttyp9    00:00:00 tcsh
6642 ttyp9    00:00:00 ps
```

ps命令显示的子进程标记为“defunct”即，僵死进程

杀死父进程，从而让init回收子进程

# 非终止
子进程

```
void fork8() {
    if (fork() == 0)       /* Child */
        printf("Running Child, PID = %d\n",
               getpid());
        while (1)           ; /* Infinite loop */
    } else {
        printf("Terminating Parent, PID = %d\n",
               getpid());
        exit(0);
    }
}
```

```
linux> ./forks 8
Terminating Parent, PID = 6675
Running Child, PID = 6676
linux> ps
    PID TTY          TIME CMD
   6585 ttyp9    00:00:00 tcsh
   6676 ttyp9    00:00:06 forks
   6677 ttyp9    00:00:00 ps
linux> kill 6676
linux> ps
    PID TTY          TIME CMD
   6585 ttyp9    00:00:00 tcsh
   6678 ttyp9    00:00:00 ps
```

- 父进程终止，但子进程仍处于活动状态
- 必须明确地杀死子进程，否则将无限持续地运行

# 与子进程同步：wait

- 父进程通过wait函数回收子进程
- int wait(int *child_status)
  - 挂起当前进程的执行直到它的一个子进程终止
  - 返回已终止子进程的 pid
  - 如 child status != NULL, 则在该指针指向的整型量中写入关于终止原因和退出状态的信息):
    - 用wait.h头文件中定义的宏来检查
      - WIFEXITED, WEXITSTATUS, WIFSIGNALED, WTERMSIG, WIFSTOPPED, WSTOPSIG, WIFCONTINUED

# 与子进程同步：wait示例1

```
void fork9() {
    int child_status;

    if (fork() == 0) {
        printf("HC: hello from child\n");
        exit(0);
    } else {
        printf("HP: hello from parent\n");
        wait(&child_status);
        printf("CT: child has terminated\n");
    }
    printf("Bye\n");
}
```

![](img/7ab811dea080313a753fa0ae68528fa9_1377_0.png)

forks.c

可能的输出：
HC
HP
CT
Bye

不可能的输出：
HP
CT
Bye
HC

# 与子进程同步：wait示例2

- 子进程完成结束的顺序是任意的（没有固定的顺序）
- 可用宏函数 **WIFEXITED** 和 **WEXITSTATUS** 获取进程的退出状态信息

```
void fork10() {
    pid_t pid[N];
    int i, child_status;
    for (i = 0; i < N; i++)
        if ((pid[i] = fork()) == 0) {
            exit(100+i); /* Child */
        }
    for (i = 0; i < N; i++) { /* Parent */
        pid_t wpid = wait(&child_status);
        if (WIFEXITED(child_status))
            printf("Child %d terminated with exit status %d\n",
                   wpid, WEXITSTATUS(child_status));
        else
            printf("Child %d terminate abnormally\n", wpid);
    }
}
```
