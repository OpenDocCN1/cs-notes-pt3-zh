# Specific Cases of Alignment (x86-64)

+   - **1 byte: `char`, …**
+     - no restrictions on address
+   - **2 bytes: `short`, …**
+     - lowest 1 bit of address must be 0₂
+   - **4 bytes: `int`, `float`, …**
+     - lowest 2 bits of address must be 00₂
+   - **8 bytes: `double`, `long`, `char *`, …**
+     - lowest 3 bits of address must be 000₂