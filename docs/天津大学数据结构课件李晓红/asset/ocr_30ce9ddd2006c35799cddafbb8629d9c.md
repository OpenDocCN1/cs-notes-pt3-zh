# # 希尔排序的算法

```
typedef int SortData;
void ShellSort ( SortData V[] , int n ) {
    SortData temp; int gap = n / 2;   //gap是间隔
    while ( gap != 0 ) {   //循环,直到gap为零
        for ( int i = gap; i < n; i++ ) {
            temp = V[i];   //直接插入排序
            for ( int j = i; j >= gap; j = j-gap )
                if ( temp < V[j-gap] )
                    V[j] = V[j-gap];
                else break;
                V[j] = temp;
        }
        gap = ( int ) ( gap / 2 );
    }
}
```