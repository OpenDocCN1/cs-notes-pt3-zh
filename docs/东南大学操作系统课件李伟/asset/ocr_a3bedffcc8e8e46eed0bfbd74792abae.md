# # Segmentation Architecture

+   - Logical address consists of a two tuple:
+     - `<segment-number, offset>`

+   - *Segment table* – maps two-dimensional to physical addresses; each table entry has:
+     - *base* – contains the starting physical address where the segments reside in memory.
+     - *limit* – specifies the length of the segment.