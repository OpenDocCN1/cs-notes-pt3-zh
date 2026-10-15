# mm_alloc()

```
1. static void *find_fit(size_t asize)
2. {
3.     void *bp ;
4.
5.     /* first fit search */
6.     for (bp = heap_listp; GET_SIZE(HDRP(bp)) > 0 ; bp = NEXT_BLKP(bp) ) {
7.         if (!GET_ALLOC(HDRP(bp)) && (asize <= GET_SIZE(HDRP(bp)))) {
8.             return bp;
9.         }
10.    }
11.    return NULL; /*no fit */
12. }
```