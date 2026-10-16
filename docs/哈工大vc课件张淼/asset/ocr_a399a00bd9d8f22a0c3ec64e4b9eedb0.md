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

栈内存

①

a
 a.x
 a.p