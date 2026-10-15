# ELF Symbol Tables

```
1. typedef struct {
2.     int name ;     /* string table offset */
3.     int value ;    /* section offset, or VM address */
4.     int size ;     /* object size in bytes */
5.     char type:4 , /* data, func, section, or src file name */
6.         binding:4 ; /* local or global */
7.     char reserved ;/* unused */
8.     char section ; /* section header index, ABS, UNDEF, */
9.                 /* or COMMON */
10. }
```

+   - ABS, UNDEF, COMMON