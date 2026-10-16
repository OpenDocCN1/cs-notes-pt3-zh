Now the ideas of erasing list:
Decrement the reference count by 1, if it becomes 0, then examining the top level nodes, any sublists encountered are erased and finally, the top level nodes are linked into the av list.

```
~GenList
// Driver
template <class T>
GenList::~GenList()
{ // Each head node has a reference count.
    if (first) { Delete(first); first = 0;}
}
```