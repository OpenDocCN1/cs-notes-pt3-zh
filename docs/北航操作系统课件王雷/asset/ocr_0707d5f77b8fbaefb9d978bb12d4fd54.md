# 软件实现进程互斥 4

```
flag[i] := true;  turn := j;
while (flag[j] && turn == j) do skip;
critical section;
flag[i] := false;
remainder section;
```

+   - 在进入区先修改后检查，并检查并发修改的先后：(Peterson algorithm)
+   - 检查对方flag，如果不在临界区则自己进入——空闲则入
+   - 否则再检查turn：保存的是较晚的一次赋值，则较晚的进程等待，较早的进程进入——先到先入，后到等待