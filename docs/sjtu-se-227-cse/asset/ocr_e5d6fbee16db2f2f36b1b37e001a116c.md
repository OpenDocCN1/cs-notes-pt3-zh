# Implement Preemptive Scheduling

+   - Set the interval timer of a clock device
+   - When the timer expires
+     - The clock triggers an interrupt
+     - Switching to kernel mode in the processor layer to invoke clock interrupt handler
+   - The clock interrupt handler invokes an exception handler
+     - Runs in the thread layer
+     - Forces the currently running thread to yield