# 异常处理

```
double Div(double, double);
void main()
{
    try{
        cout <<"7.3/2.0=" <<Div(7.3, 2.0) <<endl;
        cout <<"7.3/0.0=" <<Div(7.3, 0.0) <<endl;
        cout <<"7.3/1.0=" <<Div(7.3, 1.0) <<endl;
    }
    catch(double)
    {
        cout <<"exception of deviding zero.\n";
    }
    cout <<"That is ok. \n";
}
double Div(double a, double b)
{
    if(b==0.0)
        throw b;
    return a/b;
}
```

如果发生异常则只中断try里面块

try和catch必须相邻；顺序不能颠倒

参数可以省略但是类型不能省略；

类型匹配必须严格类型相同；

Throw和catch可以跨函数放置