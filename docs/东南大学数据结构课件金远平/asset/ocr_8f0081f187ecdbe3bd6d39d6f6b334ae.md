| leftChild | data | rightChild |

![](bbox=[0.6, 0.05, 0.92, 0.35])

```
template <class T>
class Tree {
public:
    // Tree operations
    ...
private:
    TreeNode<T>* root;
};
```

If necessary, a 4th field, parent, may be included in the node.