# Variable-Length Records: Slotted Page Structure

![](bbox=[0.13, 0.135, 0.92, 0.475])

+   - Slotted page header contains:
+     - number of record entries
+     - end of free space in the block
+     - location and size of each record
+   - Records can be moved around within a page to keep them contiguous with no empty space between them; entry in the header must be updated.
+   - Pointers should not point directly to record — instead they should point to the entry for the record in header.