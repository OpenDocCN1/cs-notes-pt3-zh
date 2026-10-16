# 3.2 二叉树（Cont.）

```
void Exchange ( BREE T )
{
    struct node *p,*tmp;
    top = -1;    //采用顺序栈，并假定不会发生上溢
    if ( T != NULL ) {
        s[++top] = T;
        while ( top != -1 ) {
            p = s[top--]; //栈中退出一个结点
            tmp = p->lchild //交换子女
            p->lchild = p->rchild;
            p->rchild = tmp;
            if ( p->lchild != NULL )
                s[++top] = p->lchild;
            if ( p->rchild != NULL )
                s[++top] = p->lchild;
        }使用栈消去递归算法中的两个递归语句
    }
}
```

```
struct node {
    struct node *lchild ;
    struct node *rchild ;
    datatype data ;
};
typedef node * BTREE ;
```