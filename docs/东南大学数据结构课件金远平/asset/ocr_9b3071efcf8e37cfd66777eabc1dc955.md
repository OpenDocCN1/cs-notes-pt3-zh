```
template <class T>
void HeapSort (T *a, const int n)
{ // Sort a[1:n] into nondeceasing order.
    for (int i=n/2; i>=1; i--)  // convert list into a heap
        Adjust(a, i, n);
    for (i=n-1; i>=1; i--)      // sort
    {
        swap(a[1], a[i+1]);  // swap first and last of current heap
        Adjust(a, 1, i);     // recreate heap
    }
}
```