```
template <class T>
TreeNode<T>* Tree<T>::Copy(TreeNode<T>* origNode)
// workhorse
{ // Return a pointer to an exact copy of the binary
// tree rooted at origNode
if (!origNode) return 0;
return new TreeNode<T>(origNode->data,
    Copy(origNode->leftChild),
    Copy(origNode ->rightChild));
}
```

# 5.4.2 Testing Equality