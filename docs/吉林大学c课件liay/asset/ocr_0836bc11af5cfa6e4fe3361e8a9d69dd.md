# 类型转换

# 构造
析构函数

```
class aa {
    public:
        aa(int a=1){id=a;}
        int id;
};
class bb {
    public:
        bb(int a=2){id=a;}
        int id;
};
void m(aa a)
{cout<<a.id<<endl;}
void m(bb a)
{cout<<a.id<<endl;}
int main()
{  m(9); //存在二义性;
    return 0;
}//转换不能太复杂，不允许多参数，不允许间接转换
```