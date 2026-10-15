# Lowering CPU Overhead With Interrupts

+   - Instead of polling, the OS can issue a request, put the calling process to sleep, and context switch to another task
+   - When the device finishes, it will raise a hardware interrupt
+   - The CPU jumps into the OS at a pre-determined interrupt service routine (ISR) or more simply an interrupt handler
+   - The handler is just a piece of operating system code that will finish the request
+     - For example, by reading data and perhaps an error code from the device
+     - and wake the process waiting for the I/O, which can then proceed as desired