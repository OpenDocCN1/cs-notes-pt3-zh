要求：
调用a.f()时，在A::f中调用func(&a);
调用b.f()时，在A::f中调用func(&b);

```
void func(A * p)
{...}
class A
{ int x;
public:
void f(){func(?);}
void g(int i){x=i;f();}
};
A a,b;
a.f();
b.f();
```