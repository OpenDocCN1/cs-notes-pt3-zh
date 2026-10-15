# Interrupt When Yield?

+   - What happens if timer interrupt occurs when CPU is running `yield` / `yield_wait`?
+     - Problem: `t_lock` already locked
+       - When timer tries to call `yield()`, `acquire(t_lock)` will hang forever
+     - Solution: hardware mechanism to disable interrupts
+       - Disable interrupts before acquiring `t_lock`, re-enable after releasing it