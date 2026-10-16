# (2) 二叉排序树查找的算法实现

```
BiTree SearchBST(BiTree T , keytype key)
{
    if ((!T ) || ( T -> key == k )) returnT;
    else if (key<T -> key)
        (return SearchBST ( T -> lchild , key));
    // 在左子树中搜索
    else  return SearchBST (( T -> rchild , key));
    // 在右子树中搜索
}
```