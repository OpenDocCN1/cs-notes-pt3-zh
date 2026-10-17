# # Efficiency in Ray Tracing

+   - 95% of the time is spent in ray-object intersection
+   - So to increase speed
+     - write faster intersection algorithms
+     - reduce number of intersection calculations
+   - Intersection algorithms are always written to work efficiently. Reducing the number of intersection calculation is the key to increase speeds