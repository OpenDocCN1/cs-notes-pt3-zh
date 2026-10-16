# 软件实现进程互斥 3

```
flag[i] := true;
<a>
while (flag[j]) do
skip; <b>
critical section;
flag[i] := false;
remainder section;
```

+   - 类似于算法2，与互斥算法2的区别在于先修改后检查。仍防两进程同时进入临界区。

缺点：Pi和Pj可能都进入不了临界区。按下面序列执行时，会都进不了临界区：“Pi<a> Pj<a> Pi<b> Pj<b>”。即在切换自己flag之后和检查对方flag之前有一段时间，结果都切换flag，都检查不通过。