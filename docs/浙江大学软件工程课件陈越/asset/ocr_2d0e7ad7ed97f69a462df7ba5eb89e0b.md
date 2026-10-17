# 4.11 The C Preprocessor

+   - 4.11.3 Conditional Inclusion

form:

(1) #if constant
    block1
    #elif constant
    block2
    #else
    blockN
    #endif

(2) #ifdef name
    block1
    #else
    block2
    #endif

(3) #ifdef name
    block1
    #else
    block2
    #endif

example:

```
```c
#if SYSTEM==SYSU
    #define HDR “sysv.h”
#elif SYSTEM == BSD
    #define HDR “bsd.h”
#elif SYSTEM == MSDOS
    #define HDR “msdos.h”
#else
    #define HDR “default.h”
#endif
#include HDR
```
```

```
```c
#ifdef HDR
    …(block1)
#else
    …(block2)
#endif
```
```

![](bbox=[0.0, 0.0, 0.183, 1.0])