# Two-Level Paging Example

+   - A logical address (on 32-bit machine with 4K page size) is divided into:
+     - a page number consisting of 20 bits.
+     - a page offset consisting of 12 bits.
+   - Since the page table is paged, the page number is further divided into:
+     - a 10-bit page number.
+     - a 10-bit page offset.