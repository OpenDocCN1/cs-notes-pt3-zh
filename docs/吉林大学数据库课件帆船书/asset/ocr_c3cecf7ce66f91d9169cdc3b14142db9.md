# Tuning the Database Design (Cont.)

# Materialized Views

+   - Materialized views can help speed up certain queries
+     - Particularly aggregate queries
+   - Overheads
+     - Space
+     - Time for view maintenance
+       - Immediate view maintenance: done as part of update txn
+         - time overhead paid by update transaction
+       - Deferred view maintenance: done only when required
+         - update transaction is not affected, but system time is spent on view maintenance
+           - until updated, the view may be out-of-date
+   - Preferable to denormalized schema since view maintenance is systems responsibility, not programmers
+     - Avoids inconsistencies caused by errors in update programs