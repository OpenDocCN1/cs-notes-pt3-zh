# P操作原语

P操作原语：

```
void P(semaphore*s)
{ s->value--;
If s->value<0
    asleep(s->queue)
}
```

![](bbox=[0.48, 0.38, 0.88, 0.68])

asleep(s->queue):

+   (1) 执行此操作进程的PCB入s->queue尾（状态改为等待）；

+   (2) 转处理机调度程序。