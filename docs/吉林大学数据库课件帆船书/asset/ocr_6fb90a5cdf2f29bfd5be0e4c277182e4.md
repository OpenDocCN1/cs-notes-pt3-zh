# Recoverable Schedules

+   - **Recoverable schedule** — if a transaction $T_j$ reads a data item previously written by a transaction $T_i$, then the commit operation of $T_i$ **must** appear before the commit operation of $T_j$.
+   - The following schedule is not recoverable if $T_9$ commits immediately after the read(A) operation.
+   - If $T_8$ should abort, $T_9$ would have read (and possibly shown to the user) an inconsistent database state. Hence, database must ensure that schedules are recoverable.

| $T_8$ | $T_9$ |
| --- | --- |
| read (A) | |
| write (A) | |
|  | read (A) |
|  | commit |
| read (B) | |