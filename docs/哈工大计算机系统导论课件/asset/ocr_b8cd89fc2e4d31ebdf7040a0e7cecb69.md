# ## 两个连续的fork

*forks.c*

```
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
```

![](bbox=[0.331, 0.103, 0.879, 0.561])

# 可能的输出：

+   L0
+   L1
+   Bye
+   Bye
+   L1
+   Bye
+   Bye

# 不可能的输出：

+   L0
+   Bye
+   L1
+   Bye
+   L1
+   Bye
+   Bye