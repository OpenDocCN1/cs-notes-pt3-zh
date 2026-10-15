# Re-association Transformation

```
void combine7(vec_ptr v, int *dest)
{
    int i;
    int length = vec_length(v), limit = length-1;
    int *data = get_vec_start(v);
    int x = IDENT;

    /* combine 2 elements at a time */
    for (i = 0; i < limit; i+=2) {
        x = x OPER (data[i] OPER data[i+1]);
    }

    /* finish any remaining elements */
    for (; i < length; i++)
        x0 = x0 OPER data[i];

    *dest = x0 OPER x1;
}
```