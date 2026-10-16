# Supplemrnt: 高响应比优先(HRRN)算法
Highest Response-Ratio Next Scheduling

+   - **Non-preemptive scheduling algorithm.**
+   - **Response-Ratio :  R=(W+T)/T=1+W/T**
+     - W: waiting time in ready queue
+     - T: CPU burst time
+   - The process with the highest response-ratio will be scheduled next.
+   - HRRN considers the waiting time and CPU-burst time simultaneously.
+   - Time consuming, system overhead to calculate the response-ration for each processes.