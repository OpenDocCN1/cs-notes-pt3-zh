# Robust I/O

+   - Unbuffered Input and Output
+     - Transfer data directly between memory and a file, with no application-level buffering

```
#include "csapp.h"
ssize_t rio_readn(int fd, void *usrbuf, size_t count);
ssize_t rio_writen(int fd, void *usrbuf, size_t count);
return: number of bytes read (0 if EOF) or written, -1 on error
```