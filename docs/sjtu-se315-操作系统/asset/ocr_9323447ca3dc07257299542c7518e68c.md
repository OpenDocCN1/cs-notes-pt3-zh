# Assigning Vectors to IRQs

+   - Vector: index (0-255) into interrupt descriptor table
+   - Vectors usually IRQ# + 32
+     - Below 32 reserved for non-maskable intr & exceptions
+     - Maskable interrupts can be assigned as needed
+     - Vector 128 used for syscall
+     - Vectors 251-255 used for IPI