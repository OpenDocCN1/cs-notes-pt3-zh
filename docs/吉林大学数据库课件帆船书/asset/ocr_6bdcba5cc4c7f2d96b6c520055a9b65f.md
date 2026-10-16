# Physical Redo

+   - Redo information is logged **physically** (that is, new value for each write) even for operations with logical undo
+     - Logical redo is very complicated since database state on disk may not be “operation consistent” when recovery starts
+     - Physical redo logging does not conflict with early lock release