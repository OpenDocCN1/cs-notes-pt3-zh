# A circular list may be deleted in O(1):

```
template <class T>
void CircularList<T>::~CircularList()
{ // delete the circular list.
    if (last) { ChainNode <T> * first = last→link;
        last→link = av;  // (1)
        av = first; // (2)
        last = 0;
    }
}
```

![](bbox=[0.02, 0.55, 0.99, 0.92])