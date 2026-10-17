# # 类声明和成员函数定义的分离

# ## 3. 唯一包含主函数的源文件

包括所有相关头文件及main

```
```cpp
#include<iostream.h>
#include"date.h"
void main()
{
    Date a;
    a.set(2,4,1998);
    a.print();
}
```
```