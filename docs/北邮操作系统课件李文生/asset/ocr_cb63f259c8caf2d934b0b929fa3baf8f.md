# # Mutual Exclusion Machine Instructions

# ■ Advantages

+   - Applicable to any number of processes on either a single processor or multiple processors sharing main memory
+   - It is simple and therefore easy to verify
+   - It can be used to support multiple critical sections

# ■ Disadvantages

+   - Busy-waiting consumes processor time
+   - Starvation is possible when a process leaves a critical section and more than one process is waiting.
+   - Deadlock
+     - If a low priority process has the critical region and a higher priority process needs, the higher priority process will obtain the processor to wait for the critical region