# 并行计算----不知道结果

```
#include "stdio.h"
int x,y;
int f( int z){
    x=x+1 ;
    return (z*z);
}
int g( int u , int v){
    ... ...
}
void main(){
    x=0 ;
    g(x,f(2)) ;
}
```