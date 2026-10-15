# Dealing With Deadlock

Adopt some resource allocation protocol that ensures deadlock can never occur

# Deadlock prevention/avoidance

+   - Guarantee that deadlock will never occur
+   - Generally breaks one of the following conditions:
+     - Mutex, Hold-and-wait, No preemption, Circular wait

# Deadlock detection and recovery

+   - Admit the possibility of deadlock occurring and periodically check for it
+   - On detecting deadlock, abort
+     - Breaks the no-preemption condition