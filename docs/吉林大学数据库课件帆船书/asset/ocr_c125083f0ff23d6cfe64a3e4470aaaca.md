# Bottlenecks

+   - Performance of most systems (at least before they are tuned) usually limited by performance of one or a few components: these are called **bottlenecks**
+     - E.g., 80% of the code may take up 20% of time and 20% of code takes up 80% of time
+       - Worth spending most time on 20% of code that take 80% of time
+   - Bottlenecks may be in hardware (e.g., disks are very busy, CPU is idle), or in software
+   - Removing one bottleneck often exposes another
+   - De-bottlenecking consists of repeatedly finding bottlenecks, and removing them
+     - This is a heuristic