```
void Pop();
// Delete the front element of the queue.
};
```

To implement this ADT, we can use an array and two variable front and rear with front being one less than the position of the first element. So we have the following data members of Queue:

```
private:
    T* queue;
    int front,
        rear,
        capacity;
```