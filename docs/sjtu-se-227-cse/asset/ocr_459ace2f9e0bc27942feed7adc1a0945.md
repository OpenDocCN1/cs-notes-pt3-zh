# Caching: Classic Fast Path Optimization

+   - Use knowledge of workload: memory abstractions
+     - Keep common requests in a fast local memory
+     - Check the local memory every access
+   - CPU cache – Cache 1ns, Memory 100ns, 90% hit rate
+     - AverageLatency = 0.9 x 1ns + 0.1 x 100ns = 10.9 ns (100ns -> 10.9ns)
+   - Used everywhere there are memory abstractions
+     - Processors, file systems, TLBs, browsers, DNS, etc.

![](bbox=[0.75, 0.3, 0.92, 0.52])