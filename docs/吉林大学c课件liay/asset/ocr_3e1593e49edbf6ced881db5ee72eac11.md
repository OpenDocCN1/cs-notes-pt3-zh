# 使用malloc申请空间

`void *malloc(unsigned long size);`

例：

```
```c
#include “stdio.h”

#include “malloc.h”

int main()
{
    int *p,i;

    p=(int *)malloc(10*sizeof(int));
    for(i=0;i<10;i++) scanf(“%d”,p++);
    p=10;
    for(i=0;i<10;i++) printf(“%d”,p[i]);
    free(p);              //只能释放malloc申请的空间
    return 0;
}
```
```