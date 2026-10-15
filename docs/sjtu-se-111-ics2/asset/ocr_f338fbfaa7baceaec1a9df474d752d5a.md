# Wait_pid Function

```
pid_t waitpid(pid_t pid, int *status, int options);
```

+   - options
+     - WUNTRACED | WNOHANG : Suspended execution of the calling process until a process terminated or stopped child that caused the return. Also, return immediately (with a return value of 0 ) if none of the child processes in the wait-set is terminated or stopped