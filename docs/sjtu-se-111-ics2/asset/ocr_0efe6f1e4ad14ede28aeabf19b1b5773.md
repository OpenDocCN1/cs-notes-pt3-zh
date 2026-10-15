# Nasty Concurrency Bugs

+   - Incorrectly sequence of events
+     - Parent executes `fork` and kernel schedules the newly created child
+     - Child terminates and kernel delivers a SIGCHLD signal to parent
+     - Parent receives the SIGCHLD signal and runs the signal handler
+     - Signal handler calls `deletejob`
+     - Parent return from `fork` and calls `addjob`