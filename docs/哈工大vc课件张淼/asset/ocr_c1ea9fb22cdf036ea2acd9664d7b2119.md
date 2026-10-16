# 成员对象的初始化

```
class A
{
    int m;

public:
    A() { m=0; }
    A(int m1) { m=m1; }
};
```

```
class B
{
    int n;

    A a;

public:
    B() { n=0; }
    B(int n1) { n=n1; }
};
B b1,b2(1);
```