# 显式地等待信号

+   程序正确，但循环很浪费

+   改进：

```
while (!pid) /* Race! */
    pause();
```

```
while (!pid) /* Too slow! */
    sleep(1);
```

+   合适的解决方法: sigsuspend