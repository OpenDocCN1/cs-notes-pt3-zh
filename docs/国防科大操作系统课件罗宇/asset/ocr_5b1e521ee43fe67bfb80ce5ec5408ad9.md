# 算法2：设一个表示进程进入否状态的数组

Var flag: array[0..1] of boolean

```
Repeat
  While flag[j] do skip
  flag[i] = true;
  Critical section
  flag[i] = false;
  Non-critical section
Until false;
```

不满足互斥要求：当flag[]初值为0，两进程同时执行while语句时。