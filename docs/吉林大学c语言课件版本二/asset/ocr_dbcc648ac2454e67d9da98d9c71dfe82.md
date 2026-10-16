# 后序遍历过程是：

得到表达式的表达式的逆波兰表示式（运算符在两个运算分量之后）。

后序遍历算法是：

```
void postorder (treepointer p) { /*后序遍历*/
    if ( p!=NULL ) {
        postorder( p-> left );
        postorder( p-> right )
        printf("%c" , p-> data );
    }
}
```

![](bbox=[0.55, 0.35, 1.0, 0.85])

a b c / + d e f * - *