# Memory mountain main routine

```
int main()
{
    int size;                  /* Working set size (in bytes) */
    int stride;                /* Stride (in array elements) */
    double Mhz;                /* Clock frequency */
    init_data(data, MAXELEMS); /* Initialize each element in data to 1 */
    Mhz = mhz(0);              /* Estimate the clock frequency */
```