# 第八章： 模板

8-1:函数模板

```
```cpp
void swap1(int &a,int &b)
{
int temp=a;
a=b;
b=temp;
}
void swap1(float &a,float &b)
{
float temp=a;
a=b;
b=temp;
}//重载的代码完全一样 仅仅是被操作类型不同
```
```