# 友元类举例

```
class A
{
    friend class B;
    public:
        void Display()
        {cout<<x<<endl;}
    private:
        int x;
};

class B
{
    public:
        void Set(int i);
        void Display();
    private:
        A a;
};
```

```
void B::Set(int i)
{
    a.x=i;
}
void B::Display()
{
    a.Display();
}
```