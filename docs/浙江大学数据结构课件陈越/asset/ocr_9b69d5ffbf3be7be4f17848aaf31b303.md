# 路径压缩

```
SetName Find( SetType S, ElementType X )
{
    if ( S[X] < 0 ) /* 找到集合的根 */
        return X;
    else
        return S[X] = Find( S, S[X] );
}
```

先找到根；
把根变成 X 的父结点；
再返回根。

![](bbox=[0.179, 0.459, 0.524, 0.701])

![](bbox=[0.14, 0.727, 0.469, 0.864])

> 不用路径压缩
> 会死翘？