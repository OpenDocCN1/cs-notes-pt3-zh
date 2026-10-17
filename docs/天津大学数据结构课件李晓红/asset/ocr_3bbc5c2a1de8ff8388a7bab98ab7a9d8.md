# # Status SearchBST (BiTree T, KeyType kval, BiTree f, BiTree &p ) {

```
if (!T)
{
    p = f; return FALSE; } // 查找不成功
else if ( EQ(kval, T->data.key) )
{
    p = T; return TRUE; } // 查找成功
else if ( LT(kval, T->data.key) )
    return SearchBST (T->lchild, kval, T, p ); // 在左子树中继续查找
else
    return SearchBST (T->rchild, kval, T, p );
    // 在右子树中继续查找
} // SearchBST
```