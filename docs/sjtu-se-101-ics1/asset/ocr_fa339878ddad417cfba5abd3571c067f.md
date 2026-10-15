# Data Movement Example

```
int exchange(int *xp, int y)
{
    /* operator * performs deferencing */
    int x = *xp ;
    *xp = y ;
    return x ;
}
```