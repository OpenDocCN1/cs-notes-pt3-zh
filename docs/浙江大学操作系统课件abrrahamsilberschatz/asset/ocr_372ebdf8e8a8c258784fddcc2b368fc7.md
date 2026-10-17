# # 9.4.3 Memory Protection（存储保护）

+   - Memory protection implemented by associating protection bit with each frame.
+   （内存的保护由与每个页框相连的保护位来执行。）

+   - Valid-invalid bit attached to each entry in the page table （有效-无效位附在页表的每个表项中）：
+     - “valid” indicates that the associated page is in the process’ logical address space, and is thus a legal page. （“有效”表明相关的页在进程的逻辑地址空间，以及是一个合法的页。）
+     - “invalid” indicates that the page is not in the process’ logical address space.
+   （“无效”表明页不在进程的逻辑地址空间中。）