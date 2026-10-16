![](bbox=[0.0, 0.07, 0.35, 0.78])

```
#include "stdio.h"
void main() {
int u,v,r;
printf("pleace input u 、 v:");
scanf("%d%d",&u,%v);
r=v;
while ( r!=0 ){
r = u%v;
u = v;
v = r;
}
printf ( "gcd(u,v) = %5d\n"u );
}
```

运行结果演示