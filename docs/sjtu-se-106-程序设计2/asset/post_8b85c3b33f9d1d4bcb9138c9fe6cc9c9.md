
## 3、二叉树遍历

1、遍历二叉树：设 N 代表根节点，L 代表左子树，R 代表右子树。

- a. 前序（或先序）：如果二叉树为空，则操作为空；否则访问根结点；前序遍历左子树；前序遍历右子树。记为：NLR。
- b. 中序：如果二叉树为空，则操作为空；否则中序遍历左子树；访问根结点；中序遍历右子树。记为：LNR。
- c. 后序：如果二叉树为空，则操作为空；否则后序遍历左子树；后序遍历右子树；访问根结点。记为：LRN。

前序： A、L、B、E、C、D、W、X
中序： B、L、E、A、C、W、X、D
后序： B、E、L、X、W、D、C、A

![](img/af430dff16b82a0fe61ce7dee05dcf9c_579_0.png)

![](img/af430dff16b82a0fe61ce7dee05dcf9c_579_1.png)

1、遍历二叉树：续

- a. 前序分析：节点的左儿子、左孙子、左后代、……将连续输出。节点的右儿子将在节点、节点的左子树全部输出之后才输出。
- b. 中序分析：最先输出的节点是根节点的最左的左后代。将二叉树中的节点投影到水平轴线上，则得到中序遍历的序列。
- c. 后序分析：根节点（或子树的根节点）将在它的左、右子树的节点输出之后。因此，根节点（或子树的根节点）在中序序列中的序号等于它的左右子树的节点个数＋左右子树中的最先被访问的节点的序号。注意，节点、右父亲、右祖父、……将连续输出。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_580_0.png)

1、遍历二叉树：续

•前序的程序实现：

- 1、根结点进栈
- 2、结点出栈，被访问
- 3、结点的右、左儿子（非空）进栈
- 4、反复执行 2、3，至栈空为止。

![](img/af430dff16b82a0fe61ce7dee05dcf9c_581_0.png)

A进栈

A出栈 访问

C、L 进栈

L出栈 访问

E、B 进栈

B出栈 访问

E出栈 访问

C出栈 访问

D进栈

D出栈访问后，栈空结束

![](img/af430dff16b82a0fe61ce7dee05dcf9c_581_1.png)

分析：p的前序的直接后继q：1、p有左儿子，则q=该左儿子 2、p无左儿子，有右儿子，则q=该右儿子 3、p无左儿子、右儿子，搜索其祖先结点的右儿子送q。找不到结束。

## 遍历递归算法– Too easy!

```
void BiTree::Preorder(NodeType*p)
{ if(p!=NULL)
  {  cout<<p->data<<" ";
    preorder(p->lch);
    preorder(p->rch);
  }
}
```

```
void BiTree::inorder(NodeType*p)
{if(p!=NULL)
  { inorder(p->lch);
    cout<<p->data<<" ";
    inorder(p->rch);
  }
}
```

```
void BiTree::Postorder(NodeType*p)
{ if(p!=NULL)
  { preorder(p->lch);
    preorder(p->rch);
    cout<<p->data<<" ";
  }
}
```

## 4、二叉树遍历的迭代器类

- 二叉树的迭代器： Tree Iterator

```
ADT 5.3: 二叉树的迭代器类。
template <class Type> class TreeIterator {
public:
    TreeIterator ( const BinaryTree < Type > & BT ) : T( BT ), current( NULL) { }
    virtual ~TreeIterator ( ) { }
    virtual void First ( ) = 0;      // 第一个被访问的结点地址送current
    virtual void operator ++ ( ) = 0; // 下一个被访问的结点地址送current
    int operator + ( ) const{ return current != NULL;} //当前结点为空吗，为空返回 True
    const Type & operator ( ) ( ) const;
        // 返回当前结点指针 current 所指向的结点的数据值。
protected:
    const BinaryTree <Type > & T;
    const BinaryNode<Type > * current; // 指向当前结点的指针。
private:
    TreeIterator ( const TreeIterator & ) { }
    const TreeIterator & operator = ( const TreeIterator & );
};

template <class Type>
const Type & TreeIterator <Type> :: operator ( ) ( ) const {
    Exception( current == NULL, "This node is NULL!" );
    return current->GetData();
}
```

遍历二叉树： Tree Iterator： 前序的实现。

```
template <class Type> class Preorder : public TreeIterator < Type > {
public:
    Preorder( const BinaryTree < Type > & R );
    ~Preorder() {}
    void First();
    void operator ++ ();
    void Preorder_NLR ();
protected:
    Stack < const BinaryNode <Type > * > s;
};

template <class Type>
Preorder<Type> :: Preorder( const BinaryTree <Type> & R )
    : TreeIterator<Type > ( R ) { s.Push( T.Getroot() ); }

template <class Type>
void Preorder <Type> :: First () {
    s.MakeEmpty (); if ( T.Getroot() ) s.Push( T.Getroot() );
    operator ++ ();
}
    // 堆栈清空。若二叉树T非空，则根结点进栈，并得到当前结点。
```

• 遍历二叉树：设根节点初始时非空
• 后序算法：1、节点（初始时为根）进栈（标志0），沿左指针查找左儿子（标志1）
2、左儿子非空，返回1。
3、退栈。若为标志1转4，否则标志2，转5。
4、进栈转向右子树（标志2），如有右儿子非空，则转向1；空转向3。
5、标志改为3，访问节点，返回3
6、反复1到5，至栈空为止。

e.g:

![](img/af430dff16b82a0fe61ce7dee05dcf9c_586_0.png)

后序：E、L、D、C、A

- 分析：1、二叉树最先被访问的节点是二叉树中最左方的叶子。
- 2、p的后序的直接后继q：1、p是父节点的右儿子，则q=该父节点。2、p是父节点的左儿子，如果有右子树，则q=该右子树中最左的叶子。如果，无右子树，q=父节点。
- 3、p无父节点，那么q == NULL。

遍历二叉树： Tree Iterator 后序的实现

```
template <class Type> struct StNode {
    const BinaryNode<Type> * Node;
    int TimesPop;
    StNode( const BinaryNode <Type > * N = NULL ) : Node(N), TimesPop(0) { }
};
template <class Type> class Postorder : public TreeIterator < Type > {
public:
    Postorder( const BinaryTree < Type > & R );
    ~Postorder() { }
    void First();      // 后序遍历时的第一个节点的地址。
    void operator ++ (); // 后序遍历时的下一个节点的地址。
protected:
    Stack < StNode<Type> > s;
};
template <class Type>
Postorder<Type> :: Postorder(const BinaryTree<Type> & R) : TreeIterator<Type> (R)
{ s.Push( StNode<Type>( T.Getroot() ) ); }
template <class Type>
void Postorder <Type> :: First () {    // 得到第一个访问的结点地址
    s.MakeEmpty (); if ( T.Getroot() ) s.push ( StNode<Type>( T.Getroot() );
    operator ++ ();
}
// 根结点地址及标志 0 进栈, 去寻找第一个被访问的最左方的叶子。
```
