# Example of Multilevel Feedback Queue

+   Three queues:
+   - Q₀ – time quantum 8 milliseconds --highest priority
+   - Q₁ – time quantum 16 milliseconds --lower priority
+   - Q₂ – FCFS -- lowest priority

+   Scheduling
+   - A new process enters queue Q₀ which is served FCFS. When it gains CPU, it receives 8 milliseconds. If it does not finish in 8 milliseconds, the process is moved to the tail of queue Q₁.
+   - At Q₁ process is again served FCFS and receives 16 additional milliseconds. If it still does not complete, it is preempted and moved to the tail of queue Q₂.