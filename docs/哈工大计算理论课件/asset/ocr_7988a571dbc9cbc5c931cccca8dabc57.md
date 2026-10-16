# Time Hierarchy Theorem

+   Proof Idea:
+   - The important difference in the proof concerns the cost of simulating M while, at the same time, count the number of steps that the simulation is using.
+   - TM D must perform this timed simulation efficiently so that D runs in O(t(n)) while avoiding all languages decidable in o(t(n)/log t(n)) time
+   - For space complexity, the simulation introduced a constant factor overhead
+   - For time complexity, the simulation introduced a logarithmic factor overhead
+     - This is why we have 1 / log t(n) factor in the theorem
+     - No more efficient simulation is known yet