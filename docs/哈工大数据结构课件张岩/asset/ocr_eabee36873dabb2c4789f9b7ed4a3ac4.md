# 3.2 二叉树（Cont.）

```
BTREE *pre=NULL; //全局量
void InOrderTh(BTREE *p)//将二叉树 p 中序线索化
{ if( p ){ //p 非空时，当前访问的结点是 p
InOrderTh( p->lchild ); //左子树线索化
p->ltag=( p->lchild ) ? TRUE : FALSE; //左(右)孩子非空
p->rtag=( p->rchild )? TRUE : FALSE; //时,标志1,否:0
if ( pre ) { //若*p 的前驱*pre 存在
if ( pre->rtag == FASLE) // *p的前驱右标志为线索
pre->rchild=p; //令 *pre 的右线索指向中序后继
if ( p->ltag == FASLE) // *p的左标志为线索
p->lchild=pre; //令 *p的左线索指向中序前驱
}
pre = p; //令pre 是下一个访问的中序前驱
InOrderTh( p->rchild ); //右子树线索化
}
}
```