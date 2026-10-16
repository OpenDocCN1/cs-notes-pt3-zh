# Ready Queue

![](bbox=[0.035, 0.052, 0.449, 0.944])

+   - Processes in queue *i* have time quantum `2^i`
+   - When a process’ behavior changes, it may be placed (i.e., **promoted** or **demoted**) into a difference queue.
+   - Thus, when a CPU-bound process starts to use more CPU, it may be demoted to a lower queue