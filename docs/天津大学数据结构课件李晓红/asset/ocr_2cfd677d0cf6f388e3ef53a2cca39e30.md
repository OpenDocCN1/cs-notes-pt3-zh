# # 最小堆的向下调整算法

```
void FilterDown ( MinHeap *H, int start,
int EndOfHeap ) {
int i = start, j = 2*i+1; //j 是 i 的左子女
HeapData temp = H->data[i];
while ( j <= EndOfHeap ) {
if ( j < EndOfHeap && //两子女中选小者
H->data[j] > H->data[j+1] ) j++;
if ( temp <= H->data[j] ) break;
else { H->data[i] = H->data[j];
i = j; j = 2*j+1; } //向下滑动
}
H->data[i] = temp;
}
```