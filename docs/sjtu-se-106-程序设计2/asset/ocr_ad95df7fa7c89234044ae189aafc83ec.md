# 6、最优二叉树及其应用

3、赫夫曼算法的实现：使用最小化堆挑出最小的结点。

```
template<class Type>
void BestBinaryTree ( Type weight[], int n, node<Type> BestBinaryTree[], int m ) {
    // weight[1] 到 weight[n] 保存权值，weight[0] 不用。BestBinaryTree[1] 到
    // BestBinaryTree[2n-1] 保存最优二叉树，BestBinaryTree[0] 不用，m 应为 2n-1.
    node<Type> * minptr = new node<Type>; // 暂存最小值结点。
    MinHeap< node< Type > > MinHp(n); // 建立最小化堆，容量为 n 个单元，0 号单元不用。
    int j, k = m;
    for ( j = 1; j <= n; j++ )
        { minptr->setdata( weight[j] ); minptr->setorder( j ); MinHp.Insert( *minptr ); }
    for ( j = n+1; j <= m; j++ ) {
        MinHp.DeleteMin ( *minptr ); BestBinaryTree[k] = *minptr;
        MinHp.DeleteMin ( *minptr ); BestBinaryTree[k-1] = *minptr ;
        minptr->setdata( BestBinaryTree[k].data + BestBinaryTree[k-1].data, k, k -1 );
        minptr->setorder();
        k -= 2; MinHp.Insert( *minptr ); // 内部结点 b_j 插入最小化堆。
    }
    MinHp.DeleteMin ( *minptr ); BestBinaryTree[1] = *minptr; // 插入根结点。
}
```

![](bbox=[0.08, 0.85, 0.38, 0.95])

![](bbox=[0.4, 0.75, 0.9, 0.98])