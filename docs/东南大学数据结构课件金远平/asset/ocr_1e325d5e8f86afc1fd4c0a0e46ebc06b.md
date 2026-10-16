# 5.3.4 Postorder Traversal

```
template <class T>
void Tree<T>::Postorder()
{ // Driver.
    Postorder(root);
}

template <class T>
void Tree<T>::Postorder (TreeNode<T> * currentNode)
{ // Workhorse.
    if (currentNode) {
        Postorder(currentNode→leftChild);
        Postorder(currentNode→rightChild );
        Visit(currentNode);
    }
}
```