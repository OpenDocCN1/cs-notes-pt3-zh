# Out-of-Bounds Memory References

```
```c
/* This is very low-quality code.
   It is intended to illustrate bad programming practices.
   See Problem 3.43. */
char *getline()
{
    char buf[8];
    char *result;
    gets(buf);
    result = malloc(strlen(buf));
    strcpy(result, buf);
    return result;
}
```
```