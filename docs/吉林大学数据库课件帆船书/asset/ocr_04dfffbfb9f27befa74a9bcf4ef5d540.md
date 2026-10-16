# Timestamping

+   - Timestamp based concurrency-control protocols can be used in distributed systems
+   - Each transaction must be given a unique timestamp
+   - Main problem: how to generate a timestamp in a distributed fashion
+     - Each site generates a unique local timestamp using either a logical counter or the local clock.
+     - Global unique timestamp is obtained by concatenating the unique local timestamp with the unique identifier.

![](bbox=[0.05, 0.68, 0.95, 0.9])