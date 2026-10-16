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

对象产生，系统在堆栈中分配内存空间

调用构造函数，完成初始化

栈内存

堆内存

![](bbox=[0.55, 0.7, 0.95, 0.9])