# fork Example

```
int main()
{
    pid_t pid;
    int x = 1;

    pid = Fork();
    if (pid == 0) { /* Child */
        printf("child : x=%d\n", ++x);
        exit(0);
    }

    /* Parent */
    printf("parent: x=%d\n", --x);
    exit(0);
}

fork.c
```

+   - 调用一次，返回两次
+   - 并发执行
+     - 不能预测父进程与子进程的执行顺序
+   - 相同但是独立的地址空间
+     - fork返回时（第6行），x在父进程和子进程中都为1
+     - 后面，父进程和子进程对x所做的任何改变都是独立的
+   - 共享文件
+     - stdout文件在父、子进程是相同的

```
linux> ./fork
parent: x=0
child : x=2
```