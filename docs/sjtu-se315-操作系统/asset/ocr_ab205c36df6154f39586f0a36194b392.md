# Work Queues

+   - Always run by kernel threads
+     - Are scheduled by the scheduler
+   - Softirqs and tasklets run in an interrupt context; work queues have a pseudo-process context
+     - i.e., have a kernel context but no user context
+   - Because they have a pseudo-process context, they can sleep
+     - Work queues are shared by multiple devices
+     - Thus, sleeping will delay other work on the queue
+   - However, they are kernel-only; there is no user mode associated with it
+     - Don’t try copying data into/out of user space