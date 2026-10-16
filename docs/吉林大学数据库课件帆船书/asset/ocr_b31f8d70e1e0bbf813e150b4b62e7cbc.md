# Real-Time Transaction Systems

+   - In systems with real-time constraints, correctness of execution involves both database consistency and the satisfaction of deadlines.
+     - **Hard deadline** – Serious problems may occur if task is not completed within deadline
+     - **Firm deadline** - The task has zero value if it completed after the deadline.
+     - **Soft deadline** - The task has diminishing value if it is completed after the deadline.
+   - The wide variance of execution times for read and write operations on disks complicates the transaction management problem for time-constrained systems
+     - main-memory databases are thus often used
+     - Waits for locks, transaction aborts, contention for resources remain as problems even if data is in main memory
+   - Design of a real-time system involves ensuring that enough processing power exists to meet deadline without requiring excessive hardware resources.