# 继承

```
class Student{
    int m3;
public:
    int m1; void x(){m1=1,m2=2,m3=m3;}
protected:  int m2;
};
class Master : protected Student{
    int n3;
public: int n1;
void y(){m1=1,m2=2,n1=1,n2=2,n3=3;}
protected:  int n2;
};
void f(Student &a){}
void main()
{
    Master a;
    a.x();
    f(a);
    Student *p=&a;
}
```

> protected继承和private继承得到的类都不是子类
> 
> “凡是父类对象可以出现的地方，可以用子类对象代替”，不再适用