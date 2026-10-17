# 7.4.3 Heap Management

```
```c
#define NULL 0
#define MEMSIZE 8096 /* change for different sizes */
```
```

```
```c
typedef double align;
typedef union header
{ struct { union header *next;
           unsigned usedsize;
           unsigned freesize;
         } s;
  align a;
} header;
```
```

```
```c
static header mem[MEMSIZE];
static header *memptr=NULL;
```
```

![](bbox=[0.784, 0.665, 1.0, 0.999])

![](bbox=[0.0, 0.912, 0.097, 0.999])