# Locality of Reference and Working Sets

+   - All information items stored in the memory must not have equal frequency of use
+   
+     $AverageLatency = R_{hit} \times Latency_{primary} + R_{miss} \times Latency_{Secondary}$
+   
+   - If accesses to every cell of the primary and secondary devices were of equal frequency,
+   
+     $AverageLatency = \frac{S_{primary}}{S_{primary}+S_{secondary}} \times T_{primary} + \frac{S_{secondary}}{S_{primary}+S_{secondary}} \times T_{secondary}$
+   
+   - The primary device is L2 cache with 1 nanosecond latency and the secondary device is main memory with 10 nanoseconds latency
+     - 0.99 + 0.10 = 1.09 nanoseconds