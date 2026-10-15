# 错误引元

```
```cpp
class Bad_area {}; // 用于从area函数报告错误的类型

// 计算矩形面积；
// 在输出错误引元的情况下抛出一个 Bad_area 异常
int area(int length, int width)
{
    if (length<=0 || width <=0) throw Bad_area();
    return length*width;
}
```
```