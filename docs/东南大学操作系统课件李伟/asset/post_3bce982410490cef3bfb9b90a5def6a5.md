
# Outline

- Process Concept
- **Process Scheduling**
- Operations on Processes
- Interprocess Communication
- Communication in Client-Server Systems

# Process Scheduling Queues

- **Job queue** – set of all processes in the system
- **Ready queue** – set of all processes residing in main memory, ready and waiting to execute
- **Device queues** – set of processes waiting for an I/O device
- Process migration between the various queues

# Ready Queue And Various I/O Device Queues

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_149_0.png)

# Representation of Process Scheduling

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_150_0.png)

# Schedulers

- **Long-term scheduler** (or job scheduler) – selects which processes should be loaded into memory for execution.
- **Short-term scheduler** (or CPU scheduler) – selects which process should be executed next and allocates CPU.
- **Medium-term scheduler** – remove processes from memory and reintroduce them into memory later (**swapping**).

# Schedulers

- Short-term scheduler is invoked very frequently (milliseconds) ⇒ (must be fast).
- Long-term scheduler is invoked very infrequently (seconds, minutes) ⇒ (may be slow).
- The long-term scheduler controls the *degree of multiprogramming* (the number of processes in memory).

# Medium-Term Scheduling

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_153_0.png)

# Context Switch

- What is a process context?
  - The *context* of a process is represented in the PCB of the process and includes the values of CPU registers, the process state, the program counter, and other memory/file management information.

# CPU Switch From Process to Process

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_157_0.png)

# Exercise

- 下列哪一种情况不会引起进程之间的切换？
- A. 进程调用本程序中定义的函数进行计算
- B. 进程处理I/O请求
- C. 进程创建子进程并等待子进程结束
- D. 产生中断

# Outline

- Process Concept
- Process Scheduling
- Operations on Processes
- Interprocess Communication
- Communication in Client-Server Systems

# Process Creation

- Parent process create children processes, which, in turn create other processes, forming a tree of processes.
- A unique process identifier (an integer number) is used to identify process.

# Processes Tree on Solaris

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_161_0.png)

Root parent process for all user processes

# Process Creation

- Resource sharing
  - Parent and children share all resources.
  - Children share subset of parent’s resources.
  - Parent and child share no resources.
- Execution
  - Parent and children execute concurrently.
  - Parent waits until children terminate.

# Process Creation

- **Address space**
  - Child duplicate of parent.
  - Child has a program loaded into it.

- **UNIX examples**
  - **fork() system call** creates new process
  - **exec() system call** used after a fork to replace the process’s memory space with a new program.

# Process Creation (UNIX)

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_164_0.png)

```
pid = fork();
if (pid < 0) {/*error occured*/
    fprintf(stderr, "Fork failed");
    exit(-1);}
else if(pid == 0){/*child process*/
    execlp("/bin/ls","ls",NULL);
}
else {/*parent process*/
    wait(NULL);
    printf("Child Complete");
    exit(0);
}
```

# 作业3

下列程序的输出是什么？

```
```c
#include <sys/wait.h>
#include <sys/types.h>
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
int value = 5;
int main()
{  pid_t pid;
   pid = fork();
   if (pid == 0) {  printf("child process, value1 : %d\n", value);
                    value += 15;
                    printf("child process, value2 : %d\n", value);}

   else if (pid > 0) { printf("parent process, value3 : %d\n", value);
                       wait(NULL);
                       printf("parent process, value4 : %d\n", value);
                       exit(0);  }
}
```
```
