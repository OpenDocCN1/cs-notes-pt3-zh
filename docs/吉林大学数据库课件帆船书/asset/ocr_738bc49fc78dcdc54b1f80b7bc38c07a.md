![](bbox=[0.05, 0.02, 0.15, 0.1])

# # Long Duration Transactions

Traditional concurrency control techniques do not work well when user interaction is required:

+   - Long duration: Design edit sessions are very long
+   - Exposure of uncommitted data: E.g., partial update to a design
+   - Subtasks: support partial rollback
+   - Recoverability: on crash state should be restored even for yet-to-be committed data, so user work is not lost.
+   - Performance: fast response time is essential so user time is not wasted.