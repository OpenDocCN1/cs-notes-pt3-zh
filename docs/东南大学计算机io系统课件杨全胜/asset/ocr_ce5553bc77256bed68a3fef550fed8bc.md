# 4.1 Basic Interrupt System

# Design Issues

+   - Two design issue in implementing interrupt I/O
+     - There are multiple I/O module, how does the processor determine which device issued the interrupt?
+     - If multiple interrupts have occurred, how does the processor decide which one to process?

+   - Three general categories of techniques are in common use:
+     - Software poll
+     - Daisy chain(hardware poll, vectored)
+     - Bus arbitration(vectored)