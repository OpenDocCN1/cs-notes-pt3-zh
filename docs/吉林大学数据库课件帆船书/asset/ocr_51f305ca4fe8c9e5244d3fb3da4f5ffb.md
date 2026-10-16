# Timestamp-Based Protocols (Cont.)

+   - The timestamp ordering protocol ensures that any conflicting **read** and **write** operations are executed in timestamp order.
+   - Suppose a transaction Tᵢ issues a **read**(Q)
+     1. If TS(Tᵢ) ≤ **W**-timestamp(Q), then Tᵢ needs to read a value of Q that was already overwritten.
+        - Hence, the **read** operation is rejected, and Tᵢ is rolled back.
+     2. If TS(Tᵢ) ≥ **W**-timestamp(Q), then the **read** operation is executed, and R-timestamp(Q) is set to **max**(R-timestamp(Q), TS(Tᵢ)).