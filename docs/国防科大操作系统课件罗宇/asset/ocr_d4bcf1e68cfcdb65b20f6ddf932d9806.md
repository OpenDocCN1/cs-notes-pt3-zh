# 算法3：设一个表示进程状态的数组

Var flag: array[0..1] of boolean

```
Repeat
flag[i] = true;
While flag[j] do skip;
Critical section
flag[i] = false;
Non-ritical section
Until false;
```

不满足准则4：当若干进程欲进入临界段时，应能在有限时间内选出一个进程进入其临界段。（两进程同时置flag[]）