# 对局部性的定性评价

+   声明: 能够查看程序代码并对程序局部性有定性的认识，是专业程序员的一项关键技能。

+   问题: 关于数组 a，函数 sum_array_rows 具有良好的局部性吗？

```
int sum_array_rows(int a[M][N])
{
    int i, j, sum = 0;

    for (i = 0; i < M; i++)
        for (j = 0; j < N; j++)
            sum += a[i][j];
    return sum;
}
```