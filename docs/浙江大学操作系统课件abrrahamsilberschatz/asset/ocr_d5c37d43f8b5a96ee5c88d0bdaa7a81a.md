# # Process Scheduling (Cont.)

+   - Linux implements the FIFO and round-robin real-time scheduling classes; in both cases, each process has a priority in addition to its scheduling class.
+     - The scheduler runs the process with the highest priority; for equal-priority processes, it runs the longest-waiting one
+     - FIFO processes continue to run until they either exit or block
+     - A round-robin process will be preempted after a while and moved to the end of the scheduling queue, so that round-robin processes of equal priority automatically time-share between themselves.