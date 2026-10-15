# MSD string sort problem

Observation 1. Much too slow for small subarrays.

+   - Each function call needs its own count[] array.
+   - ASCII (256 counts): 100x slower than copy pass for N=2.
+   - Unicode (65536 counts): 32000x slower for N=2.

Observation 2. Huge number of small subarrays because of recursion.

![](bbox=[0.75, 0.18, 0.95, 0.92])