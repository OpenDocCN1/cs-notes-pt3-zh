# 递归函数

+   - 直接或间接调用自己的函数被称为递归函数
+     - 递归函数必须定义一个停止条件（基本情况）

```
int rgcd( int v1, int v2 )
{
    if ( v2 != 0 )
        return rgcd( v2, v1%v2 );
    return v1;
}
```