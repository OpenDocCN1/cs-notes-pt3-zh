# 浮点数相等判断

Demo 6: A simple example of float

```
#include <math.h>
#include <float.h>
main(){
    float f = 0.11f, int = i;
    for(i = 0; i<5; i++){
        f += 0.11f;
        if(f == 0.33f) /* wrong way */
        /* if(fabs(f-0.33f)<FLT_EPSILON) */
            printf("Equal");
    }
}
```