# Analyzing algorithm

+   M₂ = “On input ...
+   1. Scan across the ... a 1.
+   2. Repeat as long ...
+   3. Scan acr ... number of 0s and 1s ... is even or odd. If it is odd, reject.
+   4. Scan again across the tape, crossing off every other 0 starting with the first 0, and then crossing off every other 1 starting with the first 1.
+   5. If no 0s and no 1s remain on the tape, accept. Otherwise, reject.”

On stage 4, the machine crosses off at least half the 0s and 1s each time it is executed. So at most iterations of the repeat loop occur before all get crossed off.

Each scan uses O(n) steps.