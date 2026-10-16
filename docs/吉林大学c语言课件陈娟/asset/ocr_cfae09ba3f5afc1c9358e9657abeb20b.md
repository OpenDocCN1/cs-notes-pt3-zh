```
#include "stdio.h"
#include "math.h"
#define eps 1e-6
void main(){
    float x0,x1;
    x0=0.0;
    x1=0.0;
    do{
        x0=x1;
        x1=2*x0*x0*x0 +0.5*x0*x0 +0.093;
    }while(fabs(x1-x0)>eps);
    printf("x=%f\n",x0);
}
```

演示例5.8程序