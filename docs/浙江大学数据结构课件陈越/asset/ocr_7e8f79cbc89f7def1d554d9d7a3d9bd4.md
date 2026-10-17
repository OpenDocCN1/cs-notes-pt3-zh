# （2）中序遍历

遍历过程为：

+   ① 中序遍历其左子树；

+   ② 访问根结点；

+   ③ 中序遍历其右子树。

中序遍历=> D B E F A G H C I

void InOrderTraversal( BinTree BT )
{
    if( BT ) {
        InOrderTraversal( BT->Left );
        printf("%d", BT->Data);
        InOrderTraversal( BT->Right );
    }
}

![](bbox=[0.644, 0.332, 0.944, 0.748])