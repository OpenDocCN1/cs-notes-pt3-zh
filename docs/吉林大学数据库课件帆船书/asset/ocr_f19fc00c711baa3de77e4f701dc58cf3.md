# External Language Routines (Cont.)

+   - Benefits of external language functions/procedures:
+     - more efficient for many operations, and more expressive power.
+   - Drawbacks
+     - Code to implement function may need to be loaded into database system and executed in the database system’s address space.
+       - risk of accidental corruption of database structures
+       - security risk, allowing users access to unauthorized data
+     - There are alternatives, which give good security at the cost of potentially worse performance.
+     - Direct execution in the database system’s space is used when efficiency is more important than security.