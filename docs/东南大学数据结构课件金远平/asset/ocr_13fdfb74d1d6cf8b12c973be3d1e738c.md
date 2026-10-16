```
```cpp
template <class T>
void Queue<T>::Push(const T & x)
{ // add x at rear of queue
    if ((rear+1)%capacity == front)
    { // queue full, double capacity
        // code to double queue capacity comes here
    }
    rear = (rear+1)%capacity;
    queue[rear] = x;
}
```
```

We can double the capacity of queue in the way as shown in the next slide: