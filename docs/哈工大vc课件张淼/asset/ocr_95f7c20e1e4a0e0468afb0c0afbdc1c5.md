```
class A
{ int x;
    char *p;
    public:
        A(char *p,int x)
        { this->p = new char[strlen(p) + 1];
          strcpy(this->p,p);
          this->x = x;}
        ~A(){delete p;}
};
void main()
{A a("lisi",23);
......}
```

对象生命周期结束，在结束前先调用析构函数

对象产生，系统在堆栈中分配内存空间

栈内存

a
 a.x 23
 a.p

对象生命周期结束，释放内存

调用构造函数，完成初始化

①

②

③

④