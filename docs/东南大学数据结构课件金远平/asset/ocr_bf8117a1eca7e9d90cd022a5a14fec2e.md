# Thus we have:

```
T* ThreadedInorderIterator::Next()
{ // Return the inorder successor of currentNode in a threaded
// binary tree
    ThreadedNode<T>* temp=currentNode→rightChild;
    if (! currentNode→rightThread)
        while (!temp→leftThread) temp=temp→leftChild;
    currentNode=temp;
    if (currentNode===root) return 0; //no next
    else return &currentNode→data;
}
```