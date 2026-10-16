# 递归——递归程序

例8-14 编一个函数 factorial 计算阶乘 n！

按过去程序设计思想，该函数应该写成：

```
int factorial ( int n ) {
    int i,p;
    p=1;
    for ( i=1 ; i<=n ; i=i+1 )
        p=p*i;
    return p ;
}
```