# Virtual-address Space

![](bbox=[0.05, 0.18, 0.38, 0.96])

Physical memory may be organized in page frames, and the physical page frames assigned to a process may not be contiguous.

It is up to the MMU to map logical pages to physical page frames in memory.

The large blank space between the heap and the stack is part of the virtual address space, but will require actual physical pages only if the heap or stack grows.