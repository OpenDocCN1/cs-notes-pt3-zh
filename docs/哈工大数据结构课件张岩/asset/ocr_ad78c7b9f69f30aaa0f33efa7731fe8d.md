# 3.2 二叉树（Cont.）

交换二叉树所有结点子树的算法.

```
void Exchange( BTREE T )
{ Node *p = T, *tmp;
    if ( p != NULL ) {
        temp = p->lchild;
        p->lchild = p->rchild;
        p->rchild = tmp;
        Exchange( p->lchild );
        Exchange( p->rchild );
    }
}
```

```
struct node {
    struct node *lchild ;
    struct node *rchild ;
    datatype data ;
};
typedef node * BTREE;
```