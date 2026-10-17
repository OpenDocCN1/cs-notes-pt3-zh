# # 算法的后期测试

在算法中的某些部位插装时间函数time（），测定算法完成某一功能所花费时间

```
```c
double start, stop;
time (&start);
int k = seqsearch (a, n, x);
time (&stop);
double runTime = stop - start;
printf ( "%d%d\n " , n, runTime );
```
```