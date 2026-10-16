# # Variable Partitions

+   - If the hole is larger than the requested size, it is cut into two. The one of the requested size is given to the process, the remaining one becomes a *new* hole.
+   - When a process returns a memory block, it becomes a hole and must be combined with its neighbors.

![](bbox=[0.203, 0.604, 0.837, 0.979])