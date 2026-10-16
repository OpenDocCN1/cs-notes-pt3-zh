# 15.关于析构函数

```
class A{
    char *p;
    public:
        A(){p=new char[5];}
virtual ~A(){delete [] p;}
};
class B:public A{
    char *q;
    public:
        B(){q=new char[500];}
        ~B(){delete [] q;}
};
void f(){A *p;p=new B;delete p;}
void main(){
    f(); f(); ... ...
}
```

析构函数为虚函数时，编译器进行运行绑定。析构函数的调用沿着继承树自下而上