# Sending Signals with kill Function

```
#include <sys/types.h>
#include <signal.h>
int kill(pid_t pid, int sig);
returns: 0 if OK, -1 on error
```

+   - If pid is greater than zero,
+     - then the kill function sends signal number sig to process pid
+   - If pid is less than zero
+     - then kill sends signal sig to every process in process group abs(pid)