# 名字空间

```
```cpp
namespace zhs{
class aa {
public:
    void aa1(int a=1){id=a;}
    int id;
};
int age;
double score;
void f(){age=1;score=80.5;}
}
namespace ls{
    void a();
}
void ls::a(){cout<<zhs::age<<endl;}
int main()
{ zhs::f();  ls::a();
    return 0;}
```
```

> 替换为：age如何？