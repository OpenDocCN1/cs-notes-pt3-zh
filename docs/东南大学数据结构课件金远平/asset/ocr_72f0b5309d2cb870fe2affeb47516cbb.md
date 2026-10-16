```
template <class T>
MaxHeap<T>::MaxHeap (int theCapacity=10)
{ //constructor
    if (theCapacity < 1) throw "Capacity must be >= 1";
    capacity = theCapacity;
    heapSize = 0;
    heap = new T[capacity+1]; //heap[0] not used
}
```

```
template <class T>
Inline T& MaxHeap<T>::Top()
{
    if (IsEmpty()) throw "The heap is empty";
    return heap[1];
}
```