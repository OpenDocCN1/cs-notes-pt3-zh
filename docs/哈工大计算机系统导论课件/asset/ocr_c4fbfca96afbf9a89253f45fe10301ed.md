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

![](bbox=[0.32, 0.22, 0.95, 0.47])