# Requirements

+   - Must save the processor’s registers for future transparent resume
+   - Must be set up for execution in the kernel
+   - Must chose a place for the kernel to start executing
+   - Must be able to retrieve information about the event, e.g., system call arguments
+   - Must all be done securely
+   - Must maintain isolation of user processes and the kernel