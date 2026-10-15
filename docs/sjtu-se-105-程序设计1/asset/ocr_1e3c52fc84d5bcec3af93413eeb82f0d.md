+   - 用未命名的名字空间声明一个局部于当前文件的实体

```
// ---- SortLib.C ----
namespace {
    void swap( double *d1, double *d2 ) {/* ... */}
}

// 四个排序函数的定义，其中使用了 swap函数
void quickSort( double *d1, double *d2 ) {/* ... */}
void bubbleSort( double *d1, double *d2 ) {/* ... */}
void mergeSort( double *d1, double *d2 ) {/* ... */}
void heapSort( double *d1, double *d2 ) {/* ... */}
```