# 例 求绝对值函数的模板

```
#include<iostream.h>

template<class T>
T abs(T x)
{    return x<0?-x:x;    }

void main()
{  int n=-5;
  double d=-5.5;
  cout<<abs(n)<<endl;
  cout<<abs(d)<<endl;
}
```