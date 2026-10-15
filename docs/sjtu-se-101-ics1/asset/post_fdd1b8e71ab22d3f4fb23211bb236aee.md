
## Linking at Running Time

- Loading and Linking Shared Libraries from Applications
  - Done explicitly by user with dlopen() in Linux

```
Unix>gcc -rdynamic -O2 -o p3 dll.c -ldl
```

## Linking at Running Time

```
#include <dlfcn.h>
void *dlopen(const char *filename, int flag);
    returns: ptr to handle if OK, NULL on error
void *dlsym(void *handle, char *symbol);
    returns: ptr to symbol if OK, NULL on error
int dlclose(void *handle);
    returns: 0 if OK, -1 on error
const char *dlerror(void);
    returns: errormsg if previous call to
dlopen, dlsym, or dlclose failed,
NULL if previous call was OK
```

```
1. #include <stdio.h>
2. #include <dlfcn.h>
3.
4. int x[2] = { 1, 2 };
5. int y[2] = { 3, 4 };
6. int z[2];
7.
• int main()
• {
•     void *handle;
•     void (*addvec)(int *, int *, int *, int );
•     char *error ;
•
```

```
14.  /*dynamically load the shared library that contains addvec() */
15.  handle = dlopen("./libvector.so", RTLD_LAZY);
16.  if (!handle) {
17.      fprintf(stderr, "%s\n", dlerror());
18.      exit();
19.  }
20.
21.  /*get a pointer to the addvec() function we just loaded */
22.  addvec = dlsym(handle, "addvec");
23.  if ( (error = dlerror()) != NULL ) {
24.      fprintf(stderr, "%s\n", error);
25.      exit(1);
26.  }
27.
```

```
28. /* Now we can call addvec() just like any other function */
29. addvec(x, y, z, 2)
30. printf("z=[%d, %d]\n", z[0], z[1]);
31.
32. /* unload the shared library */
33. if (dlclose(handle) <0) {
34.     fprintf(stderr, "%s\n", dlerror());
35.     exit(1);
36. }
37. return 0;
38. }
```

## Dynamic Memory Allocation

## Outline

- The allocation functions
- Implementation of a simple allocator
- Suggested reading: 10.9

## Dynamic Memory Allocation

- Explicit vs. Implicit Memory Allocator
  - Explicit: application allocates and frees space
    - E.g., `malloc` and `free` in C
  - Implicit: application allocates, but does not free space
    - E.g. garbage collection in Java, ML or Lisp

## Dynamic Memory Allocation

- Allocation
  - In both cases the memory allocator provides an abstraction of memory as a set of blocks
  - Doles out free memory blocks to application

Kernel virtual memory

Memory invisible to user code

User stack
(created at run time)

Memory mapped region for shared libraries

printf function

Run-time heap (created at run time by malloc)

Read/write data

Read-only code and data

0x08048000 (32)

0x00400000 (64)

0

Loaded from the hello executable file

## Malloc package

- `#include <stdlib.h>`
- `void *malloc(size_t size)`
  - if successful:
    - returns a pointer to a memory block of at least size bytes, aligned to 8-byte boundary.
    - if size==0, returns NULL
  - if unsuccessful: returns NULL
- `void free(void *p)`
  - returns the block pointed at by p to pool of available memory
  - p must come from a previous call to malloc,calloc or realloc.

## Why Dynamic Memory Allocation

```
6 int main()
7 {
8     int i, n;
9
10    scanf("%d", &n);
11    if (n > MAXN)
12        app_error("Input file too big");
13    for (i = 0; i < n; i++)
14        scanf("%d", &array[i]);
15    exit(0);
16 }
```

## Why Dynamic Memory Allocation

```
1 #include "csapp.h"
2
3 int main()
4 {
5     int *array, i, n;
6
7     scanf("%d", &n);
8     array = (int *)Malloc(n * sizeof(int));
9     for (i = 0; i < n; i++)
10        scanf("%d", &array[i]);
11    exit(0);
12 }
```

![](img/b3f8b91675c485f1e811aa092ebbf3d4_938_0.png)

Kernel virtual memory

Memory invisible to user code

User stack (created at run time)

Memory mapped region for shared libraries

`printf` function

# **`sbrk`**

# Run-time heap (created at run time by malloc)

Read/write data

Read-only code and data

Loaded from the `hello` executable file

`0x08048000 (32)`

`0x00400000 (64)`

`0`
