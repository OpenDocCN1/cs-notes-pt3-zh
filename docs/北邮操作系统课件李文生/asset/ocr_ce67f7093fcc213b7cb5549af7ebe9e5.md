# # Standard C Library Example

+   - C program invoking printf() library call, which calls write() system call

![](bbox=[0.373, 0.141, 0.955, 0.976])

```
```c
#include <stdio.h>
int main ()
{
  ⋮
  printf ("Greetings");
  ⋮
  return 0;
}
```
```

user mode

kernel mode

standard C library

write()

write() system call