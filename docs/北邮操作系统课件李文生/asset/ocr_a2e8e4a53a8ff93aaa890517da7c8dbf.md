# Scheduler Activations

+   - Both M:M and Two-level models require communication to maintain the appropriate number of kernel threads allocated to the application
+   - Scheduler activations provide **upcalls** a communication mechanism from the kernel to the thread library
+   - This communication allows an application to maintain the correct number kernel threads