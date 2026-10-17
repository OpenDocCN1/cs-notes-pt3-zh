# # 第3章 类与对象

# ## 3.2 类的定义与实现

# # 类的定义

```
class Clock
{
private :
    int hour, minute, second;    //关于时间的数据;
public :
    void setClock(int h, int m, int s);  //调整时间值 ;
    void showClock ( );    //显示时间值 ;
};
```