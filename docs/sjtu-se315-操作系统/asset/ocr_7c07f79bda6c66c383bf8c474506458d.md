# Interrupt Driven

+   - CPU sets up interrupt handler vector before I/O
+   - CPU issues I/O request and continues other tasks
+   - I/O device processes the I/O request
+   - I/O device triggers CPU interrupt-request line
+   - Interrupt handler receives interrupts and dispatches to correct handler