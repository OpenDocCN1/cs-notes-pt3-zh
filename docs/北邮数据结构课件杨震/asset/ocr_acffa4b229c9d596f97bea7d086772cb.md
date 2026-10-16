方法1：根据二叉排序树中序遍历所得结点值为增序的性质，在遍历中将当前遍历结点与其前驱结点值比较，即可得出结论。

```
void JudgeBST(BTree t,int flag)
{ //全局指针pre，初值为NULL；调用时变量flag=TRUE
    if (t!=NULL && flag)
    {
        JudgeBST(t->lc,flag);  // 中序遍历左子树
        if(pre==NULL)
            pre=t;  // 中序的第一个结点不判断
        else if(pre->data<t->data)
            pre=t;  // 前驱指针指向当前结点
        else
            flag=FLASE;    //不是完全二叉树
        JudgeBST(t->rc,flag);  // 中序遍历右子树
    }
}
```