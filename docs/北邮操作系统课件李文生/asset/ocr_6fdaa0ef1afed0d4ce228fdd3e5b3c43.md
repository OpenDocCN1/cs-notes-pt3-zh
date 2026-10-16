# Process Termination

+   - Process executes last statement and asks the operating system to delete it (via `exit`).
+     - Output data from child to parent (via `wait`).
+     - Process’ resources are deallocated by operating system.

+   - Parent may terminate execution of its children processes (via `abort`) for a variety of reasons:
+     - Child has exceeded its usage of allocated resources.
+     - Task assigned to child is no longer required.
+     - Parent is exiting.
+       - Operating system does not allow child to continue if its parent terminates.
+       - Cascading termination, normally initiated by the operating system.