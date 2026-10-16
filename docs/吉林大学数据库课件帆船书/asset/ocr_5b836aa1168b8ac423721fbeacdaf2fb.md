# Recovery Algorithm (Cont.)

+   **Undo phase:**
+   1. Scan log backwards from end
+      1. Whenever a log record <T_i, X_j, V_1, V_2> is found where T_i is in undo-list perform same actions as for transaction rollback:
+         1. perform undo by writing V_1 to X_j.
+         2. write a log record <T_i, X_j, V_1>
+      2. Whenever a log record <T_i start> is found where T_i is in undo-list,
+         1. Write a log record <T_i abort>
+         2. Remove T_i from undo-list
+      3. Stop when undo-list is empty
+         - i.e. <T_i start> has been found for every transaction in undo-list
+   - After undo phase completes, normal transaction processing can commence