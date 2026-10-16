# 二叉排序树的插入算法

```
Status Insert BST(BiTree &T, ElemType e )
{
    if (!SearchBST ( T, e.key, NULL, p ))
    {
        s = new BiTNode;
        s->data = e;
        s->lchild = s->rchild = NULL;
        if ( !p ) T = s;
        else if (T(e.key, p->data.key))
            p->lchild = s;
        else p->rchild = s;
        return TRUE;
    }
    else return FALSE;
}
```

// 为新结点分配空间

// 插入 s 为新的根结点

// 插入 s 为 *p 的左孩子

// 插入 s 为 *p 的右孩子

// 插入成功

// Insert BST