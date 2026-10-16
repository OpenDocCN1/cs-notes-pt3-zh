# 与子进程同步：wait示例2

+   - 子进程完成结束的顺序是任意的（没有固定的顺序）
+   - 可用宏函数WIFEXITED和WEXITSTATUS 获取进程的退出状态信息

```
void fork10() {
    pid_t pid[N];
    int i, child_status;
    for (i = 0; i < N; i++)
        if ((pid[i] = fork()) == 0) {
            exit(100+i); /* Child */
        }
    for (i = 0; i < N; i++) {/* Parent */
        pid_t wpid = wait(&child_status);
        if (WIFEXITED(child_status))
            printf("Child %d terminated with exit status %d\n", wpid, WEXITSTATUS(child_status));
        else
            printf("Child %d terminate abnormally\n", wpid);
    }
}
//forks.c
```