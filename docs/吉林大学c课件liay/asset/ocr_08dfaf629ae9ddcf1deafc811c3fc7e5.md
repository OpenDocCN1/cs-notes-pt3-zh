# 标准名字空间std

标准c++库的所有标识符都是在一个名为std的名字空间定义的。

```
std::cout<<"ok"<<"\n";
```

```
using namespace std;
```

在std中定义和声明所有标识符都可以作为全局量来使用。

```
using std::cout;  using std::string;
```

经常会用到的std成员的using声明组成一个头文件。