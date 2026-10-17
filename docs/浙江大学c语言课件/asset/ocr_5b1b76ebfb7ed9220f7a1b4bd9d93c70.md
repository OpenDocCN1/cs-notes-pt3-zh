# 5.8 Initialization of Pointer Arrays

```
/* month_name : return name of n-th month */
char *month_name(int n)
{
    static char *name[] = {
        "Illegal month",
        "january", "february", "march",
        "april", "may", "june", "july",
        "august", "september", "october",
        "november", "december"
    };
    return (n < 1 || n > 12) ? name[0] : name[n];
}
```