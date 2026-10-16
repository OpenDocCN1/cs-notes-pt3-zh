# Recovery Algorithm (Cont.)

+   - **Recovery from failure**: Two phases
+     - **Redo phase**: replay updates of **all** transactions, whether they committed, aborted, or are incomplete
+     - **Undo phase**: undo all incomplete transactions

+   - **Redo phase:**
+     1. Find last <**checkpoint** L> record, and set undo-list to L.
+     2. Scan forward from above <**checkpoint** L> record
+        1. Whenever a record <T_i, X_j, V_1, V_2> or <T_i, X_j, V_2> is found, redo it by writing V_2 to X_j
+        2. Whenever a log record <T_i **start**> is found, add T_i to undo-list
+        3. Whenever a log record <T_i **commit**> or <T_i **abort**> is found, remove T_i from undo-list