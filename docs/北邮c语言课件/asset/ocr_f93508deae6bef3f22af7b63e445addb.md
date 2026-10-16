程序如下：

```
#include <stdio.h>
main()
{int j,k;
    int a[3][3]={1, 2, 3, 4, 5, 6, 7, 8, 9}, b[3][3];
    for (j=0;j<3;j++)
        for(k=0;k<3;k++) b[j][k]=a[k][j];
    for(j=0;j<3;j++)
    {for(k=0;k<3;k++)
        printf("%6d",b[j][k]);
        printf("\n");
    }
```