# ## 3. 插入操作实现

```
void Insert( ElementType X, int i, List PtrL )
{
    int j;
    if ( PtrL->Last == MAXSIZE-1 ){ /* 表空间已满，不能插入*/
        printf( " 表满 " );
        return;
    }
    if ( i < 1 || i > PtrL->Last+2 ) {
        printf( " 位置不合法 " );
        return;
    }
    for ( j = PtrL->Last; j >= i-1; j-- )
        PtrL->Data[j+1] = PtrL->Data[j]; /*将 a~i~ 到 a~n~ 倒序向后移动*/
    PtrL->Data[i-1] = X; /*新元素插入*/
    PtrL->Last++; /*Last仍指向最后元素*/
    return;
}
```

![](bbox=[0.5059, 0.3672, 0.9727, 0.5859])