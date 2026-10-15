
## Wait_pid Function

```
pid_t waitpid(pid_t pid, int *status, int options);
```

- options
  - WNOHANG: Return immediately (with a return value of 0) if none of the child processes in the waiting set has terminated yet
  - WUNTRACED: Suspended execution of the calling process until a process terminated or stopped child that caused the return
  - WUNTRACED | WNOHANG: Suspended execution of the calling process until a process terminated or stopped child that caused the return. Also, return immediately (with a return value of 0) if none of the child processes in the wait-set is terminated or stopped

- Checking the exit status of a reaped child
  - The status argument is non-NULL
  - `waitpid` encodes status information about the child
    - that caused the return in the `status` argument.
  - The `wait.h` include file defines several macros
    - for interpreting the `status` argument

- **WIFEXITED(status)**
  - Returns true if the child terminated normally
    - via a call to exit or a return.

- **WEXITSTATUS(status)**
  - Returns the exit status of a normally terminated child.
  - This status is only defined if WIFEXITED returned true.

- **WIFSIGNALED(status)**
  - Returns true if the child process terminated because of a signal that was not caught
- **WTERMSIG(status)**
  - Returns the number of the signal that caused the child process to terminate.
  - This status is only defined if **WIFSIGNALED** returned true.

- **WIFSTOPPED(status)**
  - Returns true if the child that caused the return is currently stopped.
- **WSTOPSIG(status)**
  - Returns the number of the signal that caused the child to stop.
  - This status is only defined if **WIFSTOPPED** returned true.

```
1 #include "csapp.h"
2 #define N 2
3 
4 int main()
5 {
6     int status, i;
7     pid_t pid;
8 
9     /* Parent creates N children */
10    for (i = 0; i < N; i++)
11        if ((pid = Fork()) == 0) /* child */
12            exit(100+i);
13
/* Parent reaps N chds. in no particular order */
while ((pid = waitpid(-1, &status, 0)) > 0) {
    if (WIFEXITED(status))
        printf("child %d terminated normally with exit
               status=%d\n", pid, WEXITSTATUS(status));
    else
        printf("child %d terminated abnormally\n", pid);
}

/* The only normal term. is if there no more chds. */
if (errno != ECHILD)
    unix_error("waitpid error");

exit(0);
}
```

```
unix> ./waitpid1

child 22966 terminated normally with exit status=100

child 22967 terminated normally with exit status=101
```

```
1 #include "csapp.h"
2 #define N 2
3
4 int main()
5 {
6     int status, i;
7     pid_t pid[N+1], retpid;
8
9     /* Parent creates N children */
10     for (i = 0; i < N; i++)
11         if ((pid[i] = Fork()) == 0) /* Child */
12             exit(100+i);
13
14     /* Parent reaps N children in order */
15     i = 0;
15  while ((retpid = waitpid(pid[i++], &status, 0)) > 0) {
16      if (WIFEXITED(status))
18          printf("child %d terminated normally with exit
19              status=%d\n", retpid, WEXITSTATUS(status));
20      else
21          printf("child %d terminated abnormally\n", retpid);
22  }
23
24  /* The only normal term. is if there are no more chds. */
25  if (errno != ECHILD)
26      unix_error("waitpid error");
27
28  exit(0);
29}
```
