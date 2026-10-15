# Foreground and Background

+   - If the last argument is a "&" character
+     - parseline returns 1
+     - indicating the program should be executed in the background
+     (the shell returns to the top of the loop and waits for the next command)
+   - Otherwise
+     - parseline returns 0
+     - indicating the program should be run in the foreground
+     (the shell waits for it to complete)