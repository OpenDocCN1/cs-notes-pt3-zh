# Summary: Interrupts vs Exceptions

+   - Varying terminology but for Intel:
+     - **Interrupt** (asynchronous, device generated)
+       - Maskable: device-generated, associated with IRQs (interrupt request lines); may be temporarily disabled (still pending)
+       - Nonmaskable: some critical hardware failures
+     - **Exceptions** (synchronous, from software)
+       - Processor-detected
+         - Faults – correctable (restartable); e.g. page fault
+         - Traps – no reexecution needed; e.g. breakpoint
+         - Aborts – severe error; process usually terminated (by signal)
+       - Programmed exceptions (**software interrupts**)
+         - int (system call), int3 (breakpoint)
+         - into (overflow), bounds (address check)