```
```cpp
template <class T> class Tree;
class TreeNode {
friend class Tree<T>;
public:
    TreeNode (T& e, TreeNode<T>* left, TreeNode<T>* right)
        {data=e; leftChild=left; rightChild=right;}
private:
    T data;
    TreeNode<T>* leftChild;
    TreeNode<T>* rightChild;
};
```
```