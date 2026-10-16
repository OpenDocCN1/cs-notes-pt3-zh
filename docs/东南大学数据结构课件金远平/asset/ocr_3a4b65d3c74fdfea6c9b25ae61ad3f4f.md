# Now we can insert at the front in O(1):

```
template <class T>
void CircularList<T>::InsertFront(const T& e)
{ // insert the element e at the “front” of the circular list *this,
// where last points to the last node in the list.
    ChainNode<T>* newNode = new ChainNode<T>(e);
    if (last) { // nonempty list
        newNode→link = last→link;
        last→link = newNode;
    }
    else { last = newNode; newNode→link = newNode;}
}
```