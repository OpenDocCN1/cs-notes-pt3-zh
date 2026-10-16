# 由右至左

```
#include "stdio.h"
int x,y;
int f( int z){
    x=x+1;
    return (z*z);
}
int g( int u , int v){
    ....
}
void main(){
    x=0;
    g(x,f(2));
}
```

![](bbox=[0.45, 0.03, 0.98, 0.92])