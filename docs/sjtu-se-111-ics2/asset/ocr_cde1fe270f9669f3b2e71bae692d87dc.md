# Fork() revisted

+   - To create a new process using fork:
+     - Net result:
+       - copies are deferred until absolutely necessary (i.e., when one of the processes tries to modify a shared page).