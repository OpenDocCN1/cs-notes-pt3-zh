# # Memory Mountain Test Function

```
```c
long data[MAXELEMS]; /* Global array to traverse */

/* test - Iterate over first "elems" elements of
 *    array "data" with stride of "stride", using
 *    using 4x4 loop unrolling.
 *
 */
int test(int elems, int stride) {
    long i, sx2=stride*2, sx3=stride*3, sx4=stride*4;
    long acc0 = 0, acc1 = 0, acc2 = 0, acc3 = 0;
    long length = elems, limit = length - sx4;

    /* Combine 4 elements at a time */
    for (i = 0; i < limit; i += sx4) {
        acc0 = acc0 + data[i];
        acc1 = acc1 + data[i+stride];
        acc2 = acc2 + data[i+sx2];
        acc3 = acc3 + data[i+sx3];
    }

    /* Finish any remaining elements */
    for (; i < length; i++) {
        acc0 = acc0 + data[i];
    }
    return ((acc0 + acc1) + (acc2 + acc3));
}
mountain/mountain.c
```
```

Call test() with many combinations of elems and stride.

For each elems and stride:

+   1. Call test() once to warm up the caches.
+   
+   2. Call test() again and measure the read throughput(MB/s)