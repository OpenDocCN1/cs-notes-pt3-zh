# 2、二叉树

·二叉树的 ADT:

```
template <class Type> class BinaryTree; // 二叉树类 BinaryTree 的向前说明
template <class Type> class BinaryNode {
friend class BinaryTree < Type>;
public:
    BinaryNode ( ) : left(NULL), right(NULL) { }  // 二叉树节点的构造函数。
    BinaryNode ( Type item, BinaryNode < Type> * L = NULL, BinaryNode < Type> *
                 R = NULL ) : data(item), left(L), right(R) { }
    ~BinaryNode ( ) { }
    Type GetData ( ) const { return data; }   // 得到二叉树节点的数据值。
    BinaryNode<Type> * GetLeft( ) const { return left; }
    //得到二叉树节点的左儿子地址。
    BinaryNode<Type> * GetRight( ) const { return right; }
    //得到二叉树节点的左儿子地址。
    void SetData ( const Type & item ) { data = item; }
    // 设置二叉树节点的数据值。
    void SetLeft (BinaryNode < Type> * L ) { left = L; }
    // 设置二叉树节点的左儿子地址。
    void SetRight (BinaryNode < Type> * R ) { right = R; }
    // 设置二叉树节点的右儿子地址。
```