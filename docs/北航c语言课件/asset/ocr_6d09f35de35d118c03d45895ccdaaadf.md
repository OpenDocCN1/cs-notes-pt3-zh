例：用选择法对数组中10个整数按由小到大排序。

函数sort(array[], n)：对数组元素按由小到大排序。

主程序：输入array数组，调用 sort 函数排序，输出排序后的array数组。

```
void main()
{void sort (int array[], int n);
int a[10], i;
printf("enter array: \n");
for (i=0; i<10; i++)
scanf ("%d",&a[i]);
sort(a,10);
printf("the sorted array: \n");
for (i=0; i<10; i++)
printf (" %d ", a[i]);
}
```

由于地址传递，实参数组 a 改变