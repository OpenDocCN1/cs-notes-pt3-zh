```
Status CreateBiTree(BiTree &T)
{
    scanf(&ch);
    if (ch=='#') T = NULL;    //构造空树
    else
    {
        if(!( T=(BiTree)malloc(sizeof(BiTNode))))
            exit(OVERFLOW);        //构造新结点
        T->data=ch;
        CreateBiTree(T->lchild); //构造左子树
        CreateBiTree(T->rchild);//构造右子树
    }
    return OK;
}
```

思考题：
请编写先序非递归建立二叉树的算法

![](bbox=[0.64, 0.75, 0.78, 0.86])