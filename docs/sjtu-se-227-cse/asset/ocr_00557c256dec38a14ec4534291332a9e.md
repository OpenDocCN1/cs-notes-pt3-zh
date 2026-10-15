# Monolithic Kernel

+   - The kernel must be a trusted intermediary for the memory manager hardware,
+     - Many designers also make the kernel the trusted intermediary for all other shared devices
+       - The clock, display, disk
+     - Modules that manage these devices must be part of the kernel program
+       - The window manager, network manager , file manager
+   - Monolithic kernel
+     - Most of the operating system runs in kernel mode