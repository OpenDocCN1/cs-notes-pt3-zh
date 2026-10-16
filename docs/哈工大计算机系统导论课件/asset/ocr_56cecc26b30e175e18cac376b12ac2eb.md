# 子进程中的嵌套fork调用

forks.c

```
void fork5()
{
    printf("L0\n");
    if (fork() == 0) {
        printf("L1\n");
        if (fork() == 0) {
            printf("L2\n");
        }
    }
    printf("Bye\n");
}
```

![](bbox=[0.32, 0.13, 0.95, 0.48])

可能的输出：

+   - L0
+   - Bye
+   - L1
+   - L2
+   - Bye
+   - Bye

不可能的输出：

+   - L0
+   - Bye
+   - L1
+   - Bye
+   - Bye
+   - L2