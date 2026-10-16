# ARIES Recovery Algorithm

ARIES recovery involves three passes

+   - Analysis pass: Determines
+   - Which transactions to undo
+   - Which pages were dirty (disk version not up to date) at time of crash
+   - RedoLSN: LSN from which redo should start

+   - Redo pass:
+   - Repeats history, redoing all actions from RedoLSN
+   - RecLSN and PageLSNs are used to avoid redoing actions already reflected on page

+   - Undo pass:
+   - Rolls back all incomplete transactions
+   - Transactions whose abort was complete earlier are not undone
+   - Key idea: no need to undo these transactions: earlier undo actions were logged, and are redone as required