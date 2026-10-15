# Issues with thread-based servers

+   - Must run “detached” to avoid memory leak.
+     - Detached thread cannot be reaped or killed by other threads.
+       - resources are **automatically reaped on termination.**
+     - Default state is joinable.
+       - use `pthread_detach(pthread_self())` to make detached.