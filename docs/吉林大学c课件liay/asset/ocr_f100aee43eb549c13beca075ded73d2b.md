# 名字空间

```
namespace zhs{
class aa {
public:
void aa1(int a=1){id=a;}
int id;
};
int age;
double score;
}
namespace ls{
using zhs::age;
void a();
}
void ls::a(){cout<<age<<endl;}

int main()
{ ls::a(); return 0;}
```