# # 带参数的构造函数

```
```cpp
class Time
{
public:
    Time(int h, int m, int s )
private:
    int hour;   int min;   int sec;
};
```
```

```
```cpp
#include <iostream.h>
int main( )
{
    Time t2(8, 15, 16);
    t2.show_time( );
    return 0;
}
```
```

> > 用参数初始化列表对数据成员初始化