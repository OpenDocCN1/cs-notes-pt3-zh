设Lock为全局布尔变量，利用Test&Set指令，即可实现对临界区的加锁与解锁：

```
Repeat
while Test&Set (lock) do skip
critical section
lock = false;
non-critical section
Until false;
```