# Review

+   - Booting: enabling segment and paging
+     - Segment: set GDT & use long jmp (ljmp)
+     - Paging: temporary page table (entrypgdir) with kernel mapped at both 0x80100000 and 0x100000
+   - Different page size: 4KB vs. 4MB(2MB)