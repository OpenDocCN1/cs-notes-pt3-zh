# 5.3.5 Multilevel Queue Scheduling

+   - **Ready queue is partitioned into separate queues:**
+     - foreground (interactive)
+     - background (batch)

+   - **Each queue has its own scheduling algorithm**
+     - foreground – RR
+     - background – FCFS

+   - **Scheduling must be done between the queues.**
+     - Fixed priority scheduling; (i.e., serve all from foreground then from background). Possibility of starvation.
+     - Time slice – each queue gets a certain amount of CPU time which it can schedule amongst its processes; i.e., 80% to foreground in RR, 20% to background in FCFS