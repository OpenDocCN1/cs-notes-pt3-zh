# 运算符重载

```
class aa{
    float a;  float b;
    public:
        float &aaa(){return(a);}
        float &bbb(){return(b);}
        operator float();
};
aa::operator float() { return(a);}
void main()
{
    aa a,b;
    a.aaa()=1; a.bbb()=2;
    b.aaa()=3; b.bbb()=4;
    cout<<float(a)<<endl;
    cout<<10+a<<endl;
    cout<<a+b<<endl;
    cout<<a<<endl;}
```

类型转换运算符声明的形式：
operator 类型名 ();

没有参数，没有返回类型，（其返回类型由函数名字指定）但是函数体中必须包含return语句。

只能作为成员函数。