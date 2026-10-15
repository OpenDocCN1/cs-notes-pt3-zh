# Warning: No Process Context

+   - Interrupts (as opposed to exceptions) are not associated with particular instructions
+   - They’re also not associated with a given process (user program)
+   - The currently-running process, at the time of the interrupt, as no relationship whatsoever to that interrupt
+   - Interrupt handlers cannot sleep!