```
void BInsertSort (SqList &L)
{
    for(i=2; i<=n; ++i)
    {
        L.r[0]=L.r[i];
        low=1; high=i-1;
        While(low<=high)
        {
            mid=(low+high)/2;
            if (L[0].key<L[mid].key) high=mid-1;
            else low=mid+1; }
        for( j=i-1; j>=high+1; --j )
            L.r[j+1]=L.r[j];
        L.r[high+1]=L.r[0];
    }
}
```

折半插入排序减少了关键字的比较次数，但记录的移动次数不变，其时间复杂度与直接插入排序相同。

/*折半后的位置*/

//插入点在低半区

/* 记录后移*/

/* 插入*/