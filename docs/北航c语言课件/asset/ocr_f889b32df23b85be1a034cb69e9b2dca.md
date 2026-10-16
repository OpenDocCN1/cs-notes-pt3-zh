# 上例中如果形参数组用指针变量，则程序如下：

```
```c
main()
{
    void max_min(int *,int ,int *,int *);
    int i,arr[10]={2,4,1,6,7,32,45,75,45,90},max,min;
    for(printf("The original array="),i=0;i<10;i++)
        printf("%5d",arr[i]);

    max_min(arr,10,&max,&min);
    printf("max=%d,min=%d",max,min);
}

void max_min(int *x, int n, int *big, int *small)
{
    int i;
    *big =*small =*x;
    for(i=1; i<n; i++)
    {
        if(*big <*(x+i)) *big =*(x+i);
        if(*small >*(x+i)) *small =*(x+i); }
}
```
```