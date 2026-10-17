# # 第11章 构造函数与析构函数

# ## 4、引用成员的初始化

类的引用成员必须在成员初始化参数表中进行初始化。例：

```
class A{
private:
int mem;
int& rmem=mem;(×) public:
A();
...};
A( ):rmem(mem)
{mem=0;};
```