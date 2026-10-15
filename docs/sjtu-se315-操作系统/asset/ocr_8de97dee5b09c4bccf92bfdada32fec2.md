# I/O Instructions and Memory-Mapped I/O

+   - I/O instructions
+     - Access device’s registers through I/O port numbers
+     - Special CPU instructions dealing with I/O
+     - Example from the Intel architecture: out 0x21,AL
+   - Memory mapped I/O (MMIO)
+     - Device’s registers/memory appear in CPU’s physical address space
+     - I/O accomplished with memory load/store instructions
+     - Mapped by MMU, addresses set by hardware jumpers or programming at boot time
+     - Can be protected with page tables