# 软件实现进程互斥 1

+   - 两个进程Pi, Pj，其中Pi

+   - 设立一个公用整型变量 turn： 描述允许进入临界区的进程标识

+   - 在进入区循环检查是否允许本进程进入： turn为i时，进程Pi可进入；

+   - 在退出区修改允许进入进程标识： 进程Pi退出时，改turn为进程Pj的标识；

```
while turn != i do
critical section;
turn := j;
remainder sectio
```