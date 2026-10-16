# 6.3 快速排序（cont.）

```
int FindPivot(int i, int j) /*设A是外部数组*/
/*若A[i],...A[j]的关键字全部相同，则返回0;
否则，左边两个不同关键字中的较大者的下标。*/
{
    keytype firstkey = A[i].key; /*第1个关键字的值A[i].key*/
    int k;                     /*从左到右查找不同的关键字*/
    for ( k=i+1 ; k<=j; k++ ) /*扫描不同的关键字*/
        if ( A[k].key > firstkey ) /*选择较大的关键字*/
            return k;
        else if ( A[k].key < firstkey )
            return i;
    return 0;
}
```

| 3 | 1 | 4 | 1 | 5 | 9 | 2 | 6 | 5 | 3 |