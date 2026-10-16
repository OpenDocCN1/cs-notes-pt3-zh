```
template <class T>
void Tree<T>::Preorder(TreeNode<T>* currentNode)
{ // workhorse.
    if (currentNode) {
        Visit(currentNode);
        Preorder(currentNode->leftChild);
        Preorder(currentNode->rightChild);
    }
}
```

For the tree of Fig. 5.16, the elements are output as:

+ * * / A B C D E  (prefix)