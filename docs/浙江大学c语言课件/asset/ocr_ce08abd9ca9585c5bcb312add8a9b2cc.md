# 1.5 Character Input and Output

+   - File copying program (2nd version)

```
```c
#include <stdio.h>

/* copy input to output; 2nd version*/
main()
{
        int c;
        while((c=getchar())!=EOF)
                putchar( c);
}
```
```

> NOTE:
> 
> > `c=getchar()!=EOF`
> > is equivalent to
> > `c=(getchar()!=EOF)`