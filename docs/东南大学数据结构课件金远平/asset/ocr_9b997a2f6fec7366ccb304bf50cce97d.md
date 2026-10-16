# ADT 5.1

```
template <class T>
class BinaryTree
{ // A finite set of nodes either empty or consisting of
// a root node, left BinaryTree and right BinaryTree.
public:
    BinaryTree ();
    // creates an empty binary tree

    bool IsEmpty ();
    // return true iff the binary tree is empty

    BinaryTree(BinaryTree<T>& bt1, T& item, BinaryTree<T>& bt2);
    // creates a binary tree whose left subtree is bt1,
    // right subtree is bt2, and root node contain item.

    BinaryTree LeftSubtree();
    // return the left subtree of *this
```