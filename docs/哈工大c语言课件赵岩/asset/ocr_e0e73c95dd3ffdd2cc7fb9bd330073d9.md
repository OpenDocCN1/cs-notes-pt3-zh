# 交换法降序

```
1 ExchangeSort(int score[], int n)
2 {
3     for (i=0; i<n-1; i++)
4     {
5         for (j=i+1; j<n; j++)
6         {
7             if (score[j] > score[i])
8                 交换成绩score[j]和score[i];
9         }
10    }
11 }
```