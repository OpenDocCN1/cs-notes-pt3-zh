# (3) 后序遍历递归算法

```
Status PostOrderTraverse(BiTree T)
{
    if (T)
    {
        if(PostOrderTraverse(T->Lchild))
        if(PostOrderTraverse (T->Rchild)) return OK;
        if( Visit(T->data))
        return ERROR;
    }
}
```