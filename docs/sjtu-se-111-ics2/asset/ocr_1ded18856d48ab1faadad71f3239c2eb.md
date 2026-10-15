# Zombie

+   - When the parent reaps the terminated child
+     - the kernel passes the child’s exit status to the parent,
+     - and then discards the terminated process, at which point it ceases to exist.
+   - A terminated process that has not yet been reaped is called a **zombie**.