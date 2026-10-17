# # 例1：选择排序算法的伪码描述

```
void SelectionSort ( int List[], int N )
{ /* 将N个整数List[0]...List[N-1]进行非递减排序 */
for ( i = 0; i < N; i++ ) {
MinPosition = ScanMinFun( List, i, N-1 );
/* 从List[i]到List[N-1]中找最小元，并将其位置赋给MinPosition */
Swap( List[i], List[MinPosition] );
/* 将未排序部分的最小元换到有序部分的最后位置 */
}
}
```

抽象 ——

List到底是数组还是链表（虽然看上去很像数组）？

Swap用函数还是用宏去实现？