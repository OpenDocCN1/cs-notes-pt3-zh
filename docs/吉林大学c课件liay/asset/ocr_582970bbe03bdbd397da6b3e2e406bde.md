```
class Student{
    int m3;
    public: int m1; void x(){m1=1;m2=2;m3=3;}
    protected: int m2;
};
class Master :public Student{
    int n3;
    public: int n1; void y(){m1=1;m2=2;n1=1;n2=2;n3=3;}
    protected: int n2;
};
void f(Master &a){... ...;}
void main()
{ Student a; Master b;
    f(a);
    Master *p=&a;
    b = a;
}
```

继承

子类对象不可以
用父类对象代替