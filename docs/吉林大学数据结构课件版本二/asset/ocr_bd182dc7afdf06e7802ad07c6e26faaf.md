# 二叉树的后序遍历（L R T）的非递归算法

```
Status PostderTraverse( BiTree T)
{
    InitStack(S);
    p=T;
    While(p || !StackEmpty(S))
    {
        if(p) { tag=0; Push(S,p); p=p->lchild;}
        else
        {
            Pop(S,p);
            if(tag=0){tag=1; Push(S,p); p=p->rchild ;}
            else{
                if(! Visit(p->data)) return ERROR;
                p=null;
            }
        }
    }
    return(OK);
```