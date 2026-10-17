# 1.5 Character Input and Output

+   - Character Counting

+   - Version 1

# Version 2

```
```c
#include <stdio.h>
main()
{
    long nc;
    nc=0;
    while(getchar()!=EOF)
        ++nc;
    printf("%ld\n",nc);
}
```
```

```
```c
#include <stdio.h>
main()
{
    double nc;
    for(nc=0;getchar()!=EOF;++nc)
        ;
    printf("%.0f\n",nc);
}
```
```

++ means increment by one.

++nc → nc=nc+1

![](bbox=[0.0, 0.0, 0.193, 1.0])