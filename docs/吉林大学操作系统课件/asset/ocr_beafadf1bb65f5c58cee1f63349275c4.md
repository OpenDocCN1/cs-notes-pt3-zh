# 尝试2

```
Boolean flag[2];

P0:
Do{
    while (flag[1]);
    flag[0]=true;
    临界区
    flag[0]=false;
    其余代码
}while(1);

P1:
do{
    while (flag[0]);
    flag[1]=true;
    临界区
    flag[1]=false;
    其余代码
}while(1);

不满足互斥性: flag[0]=flag[1]=false.
```