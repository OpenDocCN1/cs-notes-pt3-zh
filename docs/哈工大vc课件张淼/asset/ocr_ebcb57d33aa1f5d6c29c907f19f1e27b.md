```
class A
{
    public:
        void f();
        void g(int i)
        {x=i;
        f();
        }
    private:
        int x,y,z;
};
```

A a,b;

![](bbox=[0.48, 0.38, 0.98, 0.72])

g(int i)