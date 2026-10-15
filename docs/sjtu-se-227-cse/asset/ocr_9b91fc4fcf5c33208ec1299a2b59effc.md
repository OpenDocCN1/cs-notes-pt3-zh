# Queuing and Overload

+   - Overload: whenever the offered load is greater than the capacity of a service for some duration
+     - E.g., 7 threads on 3 processors, must wait in queue (RUNNABLE)
+   - The queuing theory
+     - Unit is the average service time
+     - The waiting time in a queue: 1/(1-ρ), ρ is the utilization
+     - Once the utilization approaches 1, the delay will grow without bound