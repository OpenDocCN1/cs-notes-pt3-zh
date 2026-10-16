模板参数表中的参数可以有多个，多个参数间用逗号间隔。
参数值可默认

```
template <typename S, typename T=int>
S add(T a,T b)
{
    S temp=a+b;
    return(temp);
}
void main()
{
    int a=1,b=2;
    float i=5.1,j=5.2;
    cout<<add<int,int>(i,j);
    cout<<add<float>(a,b);
}
```