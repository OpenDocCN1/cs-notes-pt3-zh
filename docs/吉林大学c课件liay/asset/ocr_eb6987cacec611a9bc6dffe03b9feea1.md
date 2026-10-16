# 类型转换：

static_cast:静态转型，必须是相关类型，非多态类层次的祖孙互易，void*转换任何类型，

dynamic_cast: 动态转型，专门针对有虚函数的继承结构，将基类指针转换成想要的子类指针

const_cast: 常量转型，去掉常量性的转换。

```
使用： dynamic_cast<Derived*>(p);
    static_cast<Car*>(p);
    const char* max(const char*,const char*);
char*
    p=const_cast<char*>(max("hello","goo
d"));
```