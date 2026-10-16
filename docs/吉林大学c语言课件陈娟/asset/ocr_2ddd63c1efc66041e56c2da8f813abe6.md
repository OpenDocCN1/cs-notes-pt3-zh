# 运行结果演示

```
/*PROGRAM find leap year*/
#include "stdio.h"
void main(){
 int yy,n;
 printf("please input begin year:");
 scanf("%d",&yy);
 printf("please input the number of the leap year:");
 scanf("%d",&n);
 yy=(yy/4+1)*4;
 do{
  if( (yy%4==0)&&(yy%100!=0)||(yy%400==0) ){
   printf("year %d\t",yy);
   n--;
  }
  yy=yy+4;
 }
 while(n>0);
}
```