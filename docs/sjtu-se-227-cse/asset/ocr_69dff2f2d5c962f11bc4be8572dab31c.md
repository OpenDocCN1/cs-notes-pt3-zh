# CPU Scheduling Policy

+   - Challenge: distinguish I/O-bound and CPU-bound
+   - Look at past behavior to predict the future
+     - Linux: Priority of job is function of amount of CPU it has used
+   - Counterintuitive:
+     - More CPU a job uses/needs, the lower its priority
+     - The less CPU it uses, the higher its priority
+     - Avoids starvation problems: Not running gives you a higher priority