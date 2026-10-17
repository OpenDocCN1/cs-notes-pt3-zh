# 4.2 Functions Returning Non-integers

• calling atof():

```
```c
#include <stdio.h>
#define MAXLINE 100
main()
{
    double sum, atof(char []);
    char line[MAXLINE];
    int getline (char line[], int max);
    sum=0;
    while(getline(line,MAXLINE)>0)
        printf("\t%lf |n", sum+= atof(line));
    return 0;
}
```
```

declaration (function protype)

> or : atof();
> in old version

calling