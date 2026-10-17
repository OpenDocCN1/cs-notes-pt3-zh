# # 快速排序的算法

```
void QuickSort ( SqList &L, int low, int high ){
//在序列low~high 中递归地进行快速排序
if ( low < high ) {
    int pivotloc= Partition (L, low, high);  //划分

    QuickSort ( L, low, pivotloc-1); //对左序列同样处理
    QuickSort ( L, pivotloc+1, high); //对右序列同样处理
    }
}
```