# ## 第8章 异常处理

# ### 8.8 assert断言

断言的作用是先计算表达式 expression，如果其值为假那么它先使用标准错误流打印一条出错信息，然后调用 abort 来终止程序运行。如果expression表达式计算结果为真，则断言不产生任何作用。举例：

```
```c
#ifdef _DEBUG   //只能用于调试版
#include<assert.h>
void main( )
{
    int x=1,y=0,z;
    _ASSERT(y!=0) //一旦y==0， 程序就会报错， 并自动退出。
    z=x/y;
}
```
```