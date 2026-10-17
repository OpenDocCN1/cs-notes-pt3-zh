
```cpp
void PreOrder( BinTree T ) {
    stack S;   InitStack(&S); //递归工作栈
    BinTreeNode * p = T; Push (&S, NULL);
    while ( p != NULL ) {
        cout << p->data << endl;
        if ( p->rightChild != NULL )
            Push ( &S, p->rightChild );
        if ( p->leftChild != NULL )
            p = p->leftChild; //进左子树
        else Pop( &S, p);
    }
}
```

![](img/04e8ddadedb998b3013c751f1cd77a21_298_0.png)

## 后序遍历二叉树（非递归算法）用栈实现

### 后序遍历时使用的栈的结点定义

```cpp
typedef struct {
    BinTreeNode *ptr;   //结点指针
    enum tag { L, R } tag;   //该结点退栈标记
} StackNode;
```

`ptr   tag{L,R}`

根结点的 tag = L，表示从左子树退出，访问右子树。  
tag = R，表示从右子树退出，访问根。

```cpp
void PostOrder ( BinTree T ) {
    stack S; InitStack(&S); StackNode w;
    BinTreeNode * p = T;
    do {
        while ( p != NULL ) { //向左子树走
            w.ptr = p; w.tag = L; Push (&S, w);
            p = p->leftChild;
        }
        int continue = 1; //继续循环标记
        while ( continue && !StackEmpty(&S) ) {
            Pop (&S, w); p = w.ptr;
            switch ( w.tag ) {   //判断栈顶tag标记
            case L : w.tag = R;  Push (&S, w);
                continue = 0;
                p = p->rightChild;   break;
            case R : cout << p->data << endl;
            }
        }
    } while ( p != NULL || !StackEmpty(&S) );
    cout << endl;
}
```

## 线索二叉树 (Threaded Binary Tree)

### 结点结构

![](img/04e8ddadedb998b3013c751f1cd77a21_306_0.png)

- LeftChild
- LeftThread
- data
- RightThread
- RightChild

- LeftThread=0, LeftChild为左子女指针
- LeftThread=1, LeftChild为前驱线索
- RightThread=0, RightChild为右子女指针
- RightThread=1, RightChild为后继指针

```cpp
template <class Type> class ThreadNode {
    friend class ThreadTree<Type>;
private:
    int leftThread, rightThread;
    ThreadNode<Type> *leftChild, *rightChild;
    Type data;
public:
    ThreadNode ( const Type item )
        : data (item), leftChild (NULL),
          rightChild (NULL), leftThread (0),
          rightThread (0) { }
};
```

![](img/04e8ddadedb998b3013c751f1cd77a21_308_0.png)

### 中序线索二叉树的类定义

```cpp
template <class Type> class ThreadTree;
```

```cpp
template <class Type> class ThreadTree {
private:
    ThreadNode<Type> * root; //根
    void InThread ( ThreadNode<Type> * current,
                    ThreadNode<Type> * pre ); //建树
public:
    ThreadTree () : root (NULL) { } //构造函数
    ThreadNode<Type> *
    First ( ThreadNode<Type> * current );
    ThreadNode<Type> *
    Last ( ThreadNode<Type> * current );
    ThreadNode<Type> *
    Next ( ThreadNode<Type> * current );
    ThreadNode<Type> *
    Prior ( ThreadNode<Type> * current );
    ......
};
```

```cpp
if ( pre != NULL &&
     pre->rightChild == NULL ) {
    pre->rightChild = current;
    pre->rightThread = 1;
} //建立前驱结点的后继线索
pre = current; //前驱跟上当前指针
InThread ( current->rightChild, pre );
//递归, 右子树线索化
}
}
```

## 用双亲表示实现的树定义

```c
#define MaxSize        //最大结点个数

typedef char TreeData; //结点数据

typedef struct {      //树结点定义
    TreeData data;
    int parent;
} TreeNode;

typedef TreeNode Tree[MaxSize]; //树
```

## 左子女-右兄弟表示法

![](img/04e8ddadedb998b3013c751f1cd77a21_315_0.png)

空链域 n(k−1)+1 个

### 第一种解决方案　等数量的链域

| data | child₁ | child₂ | child₃ | …… | child_d |
|---|---|---|---|---|---|

### 第二种解决方案 树的左子女-右兄弟表示（二叉链表表示）

结点结构

| data | firstChild | nextSibling |
|---|---|---|

空链域 n+1 个

![](img/04e8ddadedb998b3013c751f1cd77a21_316_0.png)

## 森林与二叉树的转换

![](img/04e8ddadedb998b3013c751f1cd77a21_318_0.png)

### 3 棵树的森林

![](img/04e8ddadedb998b3013c751f1cd77a21_318_1.png)

### 各棵树的二叉树表示

![](img/04e8ddadedb998b3013c751f1cd77a21_318_2.png)

### 森林的二叉树表示

## 深度优先遍历

### 树的先根次序遍历

- 当树非空时：
  - 访问根结点
  - 依次先根遍历根的各棵子树
- 树先根遍历 ABEFCDG
- 对应二叉树前序遍历 ABEFCDG
- 树的先根遍历结果与其对应二叉树表示的前序遍历结果相同
- 树的先根遍历可以借助对应二叉树的前序遍历算法实现

![](img/04e8ddadedb998b3013c751f1cd77a21_320_0.png)
