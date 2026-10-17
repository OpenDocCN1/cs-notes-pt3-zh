# 第6章　多态

```
class base
{
public:
    virtual void vf1();
    virtual void vf2();
    virtual void vf3();
    void f();
};

class derived : public base
{
public:
    void vf1();        // 虚函数
    void vf2(int);     // 重载函数
    char vf3();        // error，仅返回类型不同
    void f();          // 非虚函数
};
```

```
void main()
{
    derived d;
    base *bp = &d;
    bp->vf1();        // 调用 deriver::vf1()
    bp->vf2();        // 调用 base::vf2()
    bp->f();          // 调用 base::f()
}
```