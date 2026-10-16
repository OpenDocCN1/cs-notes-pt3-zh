# 引用传递

```
```cpp
void f(const int &x)
{
    x=1; //error
}
void main()
{
    int a = 3;
    f(a);
}
```
```