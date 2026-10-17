# # Process Memory Layout

| Environment Variables, etc. |
|-----------------------------|
| Stack Segment               |
|                             |
| Heap Storage                |
| Data Segment (global and
static variables)           |
| Text Segment                |

+   - Allocates more
+   memory than needed
+   at first

+   - Heap grows towards
+   stack for dynamic
+   memory allocation

+   - Stack grows towards
+   heap when automatic
+   variables are created