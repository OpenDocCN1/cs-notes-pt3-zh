# Process Groups

```
#include <unistd.h>
pid_t getpgrp(void);
    returns: process group ID of calling process
#include <unistd.h>
pid_t setpgid(pid_t pid, pid_t pgid);
    returns: 0 on success, -1 on error
```

+   - Changes the process group of process pid to pgid
+   - If pid is zero, the PID of the current process is used
+   - If pgid is zero, the PID of the process specified by pid is used for the process group ID