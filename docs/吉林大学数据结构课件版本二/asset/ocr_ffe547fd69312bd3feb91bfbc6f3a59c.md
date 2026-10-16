# 2 求二叉树的高度

```
```c
int hight(BTree BT)
{
 //h1和h2分别是以上BT为根的左右子树的高度
 if (BT==NULL) return 0;
 else {
 h1=hight(BT->lchild);
 h2=hight(BT->right);
 return max{h1,h2}+1;
 }
}
```
```

![](bbox=[0.55, 0.15, 0.95, 0.75])