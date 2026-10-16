```
/*PROGRAM print table9*9 */
#include "stdio.h"
void main(){
    int i,j;
    for(i=1;i<10;i++){
        printf("%4d",i);
        for(j=1;j<=i;j++)
            printf("%4d",i*j);
        printf("\n");
    }
    printf("%4c",'*');
    for(i=1;i<10;i++)
        printf("%4d",i);
}
```