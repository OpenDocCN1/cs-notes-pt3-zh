# # Code

```
```c
pid_t val;
int exit_code = 0;

val=fork();
if (val > 0) {
    int stat_val;
    pid_t child_pid;
    child_pid = waitpid(val,&stat_val,0);
    printf("Child has finished: PID = %d\n", child_pid);
    if(WIFEXITED(stat_val))
        printf("Child exited with code %d\n", WEXITSTATUS(stat_val));
    else
        printf("Child terminated abnormally\n");
    exit(exit_code);
} else if (val == 0) {
    execlp("ls","ls","-l",NULL);
}
```
```