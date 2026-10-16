```
```cpp
template <typename T>
void swap1(T& a,T& b)
{
    T temp=a;
    a=b;
    b=temp;
}
void main()
{
    int a=1,b=2;
    swap1(a,b);
    cout<<a<<b<<endl;
    float i=5.1,j=5.2;
    swap1(a,j);    //错误　必须严格匹配
    cout<<i<<j<<endl;
}
```
```