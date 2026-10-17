# 7.5 File Access

eg2: read from a character file, change lower to upper.

```
```c
#include <stdio.h>

main(int argc, char *argv[])
{
    FILE *fp1, *fp2;
    char c;
    if(argc!=3)
        exit(1);
    if((fp1==fopen(*++argv,"r"))==NULL || ((fp2=fopen(*++argv,"w"))==NULL)
        exit(2);
    while((c=fgetc(fp1)) !=EOF)
        fputc(c+'A'-'a',fp2);
    fclose(fp1);
    fclose(fp2);
}
```
```

![](bbox=[0.0, 0.0, 0.194, 1.0])