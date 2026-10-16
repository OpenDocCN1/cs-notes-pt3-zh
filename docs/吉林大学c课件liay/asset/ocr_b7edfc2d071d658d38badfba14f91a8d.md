构造
析构函数

```
class aa {
public:
    aa(){f=new char[10];}
    aa(aa const & s){
    f=new char[10]; strcpy(f,s.f);}
    ~aa(){delete []f;}
    char * f;
};
int main()
{aa p;
strcpy(p.f,"Computer");
cout<<p.f<<endl;
aa q(p);
cout<<q.f<<endl;
strcpy(p.f," Software");
cout<<p.f<<q.f<<endl;
return 0;}
```