# Virtual Addressing

+   - Address translation
+     - Converting a virtual address to a physical address
+     - Requires close cooperation between the CPU hardware and the operating system
+       - HW: the memory management unit (MMU)
+         - Dedicated hardware on the CPU chip to translate virtual addresses on the fly
+       - SW: A look-up table
+         - Stored in main memory
+         - Contents are managed by the operating system