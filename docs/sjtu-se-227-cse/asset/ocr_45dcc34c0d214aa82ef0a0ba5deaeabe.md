# Kernel Stack in Linux

+   - Linux uses part of a task’s kernel-stack to store that task’s thread_info.

```
2157 union thread_union {
2158     struct thread_info thread_info;
2159     unsigned long stack[THREAD_SIZE/sizeof(long)];
2160 };
```

![](bbox=[0.24, 0.53, 0.8, 0.85])