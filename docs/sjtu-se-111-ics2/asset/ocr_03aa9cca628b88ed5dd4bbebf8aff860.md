# Implementation issues with process

+   - Server should restart accept call if it is interrupted by a transfer of control to the SIGCHLD handler
+   - Server must reap zombie children
+     - to avoid fatal memory leak

```
void sigchld_handler(int sig)
{
    while (waitpid(-1, 0, WNOHANG) > 0)
        ;
    return;
}
```