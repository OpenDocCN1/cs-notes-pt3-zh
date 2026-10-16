# Exercise

A方向过桥进程：

B方向过桥进程？

```
do{
wait(MA);
countA ++;
if (countA == 1) then wait(mutex);
signal(MA);
过桥;
wait(MA);
countA --;
if (countA == 0) then signal(mutex);
signal(MA)
} while (1);
```