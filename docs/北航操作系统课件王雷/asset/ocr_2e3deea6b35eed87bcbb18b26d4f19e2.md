# Intel PTE

![](bbox=[0.13, 0.27, 0.88, 0.38])

+   P: Present (same as “valid” bit in other architectures)
+   W: Writeable
+   U: User accessible
+   PWT: Page write transparent; external cache write-through
+   PCD: Page cache disabled (page cannot be cached)
+   A: Accessed: page has been accessed recently
+   D: Dirty (PTE only); page has been modified recently
+   L: L=1⇒4MB page (directory only).
+   Bottom 22 bits of virtual address serve as offset