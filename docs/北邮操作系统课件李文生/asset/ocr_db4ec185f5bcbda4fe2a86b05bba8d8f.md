# 5.3.2 Shortest-Job-First (SJF) Scheduling

+   - SJF algorithm associate with each process the length of its next CPU burst. Use these lengths to schedule the process with the shortest time.

+   - Two schemes:
+     - **nonpreemptive** – once CPU is given to the process, it cannot be preempted until completes its CPU burst.
+     - **preemptive** – if a new process arrives with CPU burst length less than remaining time of current executing process, preempt. This scheme is know as the **Shortest-Remaining-Time-First (SRTF)**.

+   - SJF is optimal – gives minimum average waiting time for a given set of processes.