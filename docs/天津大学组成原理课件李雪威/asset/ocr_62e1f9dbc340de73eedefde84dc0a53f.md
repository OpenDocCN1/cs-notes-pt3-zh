# Basic Optimizations

```
```c
void combine4(vec_ptr v, data_t *dest)
{
    long i;
    long length = vec_length(v);
    data_t *d = get_vec_start(v);
    data_t t = IDENT;
    for (i = 0; i < length; i++)
        t = t OP d[i];
    *dest = t;
}
```
```

+   - Move `vec_length` out of loop
+   - Avoid bounds check on each cycle
+   - Accumulate in temporary