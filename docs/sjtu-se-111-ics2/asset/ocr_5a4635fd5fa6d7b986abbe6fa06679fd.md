# Open Files

```
```c
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>

int open(char *filename, int flags, mode_t mode);
```
```

**Returns:** new file descriptor if OK, -1 on error

# flags

+   - O_RDONLY, O_WRONLY, O_RDWR (must have one)
+   - O_CREAT, O_TRUNC, O_APPEND (optional)

# mode

+   - S_IRUSR, S_IWUSR, S_IXUSR
+   - S_IRGRP, S_IWGRP, S_IXGRP
+   - S_IROTH, S_IWOTH, S_IXOTH