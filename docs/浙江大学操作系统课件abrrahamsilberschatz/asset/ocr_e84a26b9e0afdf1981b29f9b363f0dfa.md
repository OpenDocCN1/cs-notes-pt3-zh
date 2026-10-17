# 9.4.4.2 Hashed Page Tables

+   - **Common in address spaces > 32 bits.**
+     公用地址空间大于32位

+   - **The virtual page number is hashed into a page table. This page table contains a chain of elements hashing to the same location.**
+     虚拟页的数值被散列到一个页表中，这个页表包含散列到相同地址的一根链指针。

+   - **Virtual page numbers are compared in this chain searching for a match. If a match is found, the corresponding physical frame is extracted.**
+     通过这个链搜索匹配虚页数值，如果匹配成功，取出相应的物理页框。