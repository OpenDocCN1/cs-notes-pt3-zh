# what's going to happen when the kernel enables paging?

+   - virtual address translation comes into effect?
+     - presumably the enabling instruction has address 0x100xxx
+     - 0x100xxx maps to user memory, not kernel instructions!
+     - solution
+       - temporary page table with kernel mapped at both 0x80100000 and 0x100000
+       - that's what the first few kernel instructions set up