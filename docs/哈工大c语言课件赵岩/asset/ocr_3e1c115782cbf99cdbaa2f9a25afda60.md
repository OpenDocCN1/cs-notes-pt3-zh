# 选择法排序

```
1 SelectionSort(int score[], int n)
2 {
3     for (i=0; i<n-1; i++){
4         k = i;
5         for (j=i+1; j<n; j++){
6             if (score[j] > score[k]){
7                 记录此轮比较中最高分的元素下标
8                 k = j;
9             }
10            若此轮记录的最大数不在位置i，则
11            交换成绩score[j]和score[i],
12     }
13 }
```