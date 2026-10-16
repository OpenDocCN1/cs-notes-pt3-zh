# Internal file structure

+   - **Logical structure**
+     - Two types
+       - Text file: a sequence of 8-bit bytes
+       - Record file: a sequence of records with fixed or variable length
+     - Logical address
+       - Offset from the beginning of the file
+       - Logic record no.

+   - **Physical structure: A set of disk blocks**

+   - **Basic I/O functions operate in terms of blocks**

+   - **Mapping logical address to physical address**
+     - Logical block no.
+     - Physical disk block no.
+     - Offset in block

+   - **Internal fragmentation**