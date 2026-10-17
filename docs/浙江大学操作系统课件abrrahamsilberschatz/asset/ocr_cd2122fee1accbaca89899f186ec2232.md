# # 7.4.2 Semaphore Implementation

+   - Define a semaphore as a record
+     typedef struct {
+       int value;
+       struct process *L;
+     } semaphore;

+   - Assume two simple operations:
+     - block suspends the process that invokes it.
+     - wakeup(P) resumes the execution of a blocked process P.