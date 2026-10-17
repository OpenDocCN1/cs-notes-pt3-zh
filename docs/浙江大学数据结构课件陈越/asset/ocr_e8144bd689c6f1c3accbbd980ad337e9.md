# （2）集合的并运算

+   - 分别找到X1和X2两个元素所在集合树的根结点
+   - 如果它们不同根，则将其中一个根结点的父结点指针设置成另一个根结点的数组下标。

```
void Union( SetType S[ ], ElementType X1, ElementType X2)
{
    int Root1, Root2;

    Root1 = Find(S, X1);

    Root2 = Find(S, X2);

    if ( Root1 != Root2 ) S[Root2].Parent = Root1;
}
```

> 当X1和X2不属于同一子集时，才需要合并