如:数学表达式 y=|3sinx+4cosx|+e^x,可以用C语言表达式表示为：

```
y=fabs(3*sin(x)+4*cos(x))+exp(x);
```

其中，fabs,sin,cos,exp都属于头文件 math.h，用到这些函数，必须在程序的预处理语句中用#include<math.h>把数学函数库包含进来。