```
```cpp
class A
{
    int x,y;

public:
    void f();

    void g();
};
```
```

```
```cpp
B b;

b.f(1);

b.f(); // error

b.A::f();
```
```

```
```cpp
class B:public A
{
    int z;

public:
    void f(int);

    void h()
    {
        f(1);
        f(); // error
        A::f();
    }
};
```
```