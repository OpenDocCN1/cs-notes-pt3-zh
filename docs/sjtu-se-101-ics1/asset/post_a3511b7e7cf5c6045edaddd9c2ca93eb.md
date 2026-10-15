
## mm_free()
```
27    else if (!prev_alloc && next_alloc) { /* Case 3 */
28        size += GET_SIZE(HDRP(PREV_BLKP(bp)));
29        PUT(FTRP(bp), PACK(size, 0));
30        PUT(HDRP(PREV_BLKP(bp)), PACK(size, 0));
31        return(PREV_BLKP(bp));
32    }
33
34    else { /* Case 4 */
35        size += GET_SIZE(HDRP(PREV_BLKP(bp))) +
36                GET_SIZE(FTRP(NEXT_BLKP(bp)));
37        PUT(HDRP(PREV_BLKP(bp)), PACK(size, 0));
38        PUT(FTRP(NEXT_BLKP(bp)), PACK(size, 0));
39        return(PREV_BLKP(bp));
40    }
41 }
```

## mm_malloc()
```
void *mm_malloc (size_t size)
{
    size_t asize; /* adjusted block size */
    size_t extendsize; /* amount to extend heap if no fit */
    char *bp;

    /* Ignore spurious requests */
    if (size <= 0)
        return NULL;

    /* Adjust block size to include overhead and alignment reqs. */
    if (size <= DSIZE)
        asize = DSIZE + OVERHEAD;
    else
        asize = DSIZE * ((size + (OVERHEAD) + (DSIZE-1)) / DSIZE);

    /* Search the free list for a fit */
    if ((bp = find_fit(asize)) != NULL) {
        place (bp, asize);
        return bp;
    }

    /* No fit found. Get more memory and place the block */
    extendsize = MAX (asize, CHUNKSIZE);
    if ((bp = extend_heap (extendsize/WSIZE)) == NULL)
        return NULL;
    place (bp, asize);
    return bp;
}
```

## mm_alloc()
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

## mm_alloc()
```
1.  static void place(void *bp, size_t asize)
2.  {
3.      size_t csize = GET_SIZE(HDRP(bp));
4.
5.      if ( (csize - asize) >= (DSIZE + OVERHEAD) ) {
6.          PUT(HDRP(bp), PACK(asize, 1));
7.          PUT(FTRP(bp), PACK(asize, 1));
8.          bp = NEXT_BLKP(bp);
9.          PUT(HDRP(bp), PACK(csize-asize, 0));
10.         PUT(FTRP(bp), PACK(csize-asize, 0));
11.     } else {
12.         PUT(HDRP(bp), PACK(csize, 1));
13.         PUT(FTRP(bp), PACK(csize, 1));
14.     }
15. }
```

## Dynamic Memory Allocation

## Outline
- Explicit Free List
- Segregated Free List
- Suggested reading: 9.9

## Explicit free lists
- Explicit list among the free blocks using pointers within the free blocks
- Use data space for link pointers
- Typically doubly linked
- Still need boundary tags for coalescing
- It is important to realize that links are not necessarily in the same order as the blocks

## Explicit free lists
![](img/b3f8b91675c485f1e811aa092ebbf3d4_1036_0.png)

## Freeing with explicit free lists
- Where to put the newly freed block in the free list
  - LIFO (last-in-first-out) policy
    - insert freed block at the beginning of the free list
    - pro: simple and constant time
    - con: studies suggest fragmentation is worse than address ordered.

## Freeing with explicit free lists
- Where to put the newly freed block in the free list
  - Address-ordered policy
    - insert freed blocks so that free list blocks are always in address order
      - i.e. addr(pred) < addr(curr) < addr(succ)
    - con: requires search
    - pro: studies suggest fragmentation is better than LIFO

## Segregated Storage
- Each size "class" has its own collection of blocks
  - Often have separate collection for every small size (2,3,4,...)
  - For larger sizes typically have a collection for each power of 2

## Simple segregated storage
- Separate heap and free list for each size class
- No splitting
- To allocate a block of size n:
  - if free list for size n is not empty,
    - allocate first block on list (note, list can be implicit or explicit)
  - if free list is empty,
    - get a new page
    - create new free list from all blocks in page
    - allocate first block on list
  - constant time
