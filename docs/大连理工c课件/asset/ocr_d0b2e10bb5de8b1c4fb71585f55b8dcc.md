# # 第3章 类与对象

# ## 3.4 构造函数和析构函数

# ### 构造函数：有参构造函数

用有参数的构造函数，用参数去给对象初始化或赋值，使得生成的对象具有不同的值。

```
```cpp
class Clock
{
private :
    int hour, minute, second;
public :
    Clock(int h , int m , int s){hour=h; minute =m; second=s; }
    void Clock::setClock (int h, int m, int s);
    void Clock::showClock ( );
};
Clock clock1(1,2,3);
Clock clock2;
```
```

> 错误，因为此时要调用默认构造函数，而系统并没有默认构造函数，因为当显示定义一个构造函数时，系统就不再生成默认构造函数

大连理工大学软件学院