# 6.3 遍历二叉树

(1) 先序遍历递归算法

```
Status PreOrderTraverse(BiTree T)
{
    if (T)
    { if( Visit(T->data))
        if(PreOrderTraverse(T->Lchild))
            if(PreOrderTraverse (T->Rchild)) return OK;
    return ERROR;
    }
}
```