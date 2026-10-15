# Macros

```
1 /* Basic constants and macros */
2 #define WSIZE 4 /* word size (bytes) */
3 #define DSIZE 8 /* double word size (bytes) */
• #define CHUNKSIZE (1<<12) /* Extend heap by this amount (bytes) */
• 
6 #define MAX(x, y) ((x) > (y)? (x) : (y))
7 
8 /* Pack a size and allocated bit into a word */
9 #define PACK(size, alloc) ((size) | (alloc))
10 
11 /* Read and write a word at address p */
12 #define GET(p) (*(unsigned int *)(p))
13 #define PUT(p, val) (*(unsigned int *)(p) = (val))
14
```