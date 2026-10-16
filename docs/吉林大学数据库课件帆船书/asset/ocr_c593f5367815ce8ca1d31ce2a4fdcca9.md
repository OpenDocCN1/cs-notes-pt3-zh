# Transaction Server Process Structure

+   - A typical transaction server consists of multiple processes accessing data in shared memory.
+   - Server processes
+     - These receive user queries (transactions), execute them and send results back
+     - Processes may be **multithreaded**, allowing a single process to execute several user queries concurrently
+     - Typically multiple multithreaded server processes
+   - Lock manager process
+     - More on this later
+   - Database writer process
+     - Output modified buffer blocks to disks continually