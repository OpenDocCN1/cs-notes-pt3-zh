# 第3章 类与对象

# 3.8 static成员

![](bbox=[0.335, 0.145, 0.644, 0.207])

```
对于类X的定义：
```cpp
class X{
public:
    char ch;
    static int s;
};
int X::s = 0;
```
```

```
对象a、b、c、d的定义：
```cpp
void f()
{ X a, b, c, d; }
```
```

![](bbox=[0.477, 0.255, 0.999, 0.651])

sizeof(X)?