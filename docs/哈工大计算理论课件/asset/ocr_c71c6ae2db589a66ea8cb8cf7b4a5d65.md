# Analyzing algorithm

+   **M₃ = “On input string *w* in tape 1:**
+   1. Scan across the **tape 1** and *reject* if a 0 is found to the right of a 1.
+   2. Scan across the 0s on **tape 1** until the first 1. At the same time, copy the 0s onto **tape 2**.
+   3. Scan across the 1s on **tape 1** until the end of the input. For each 1 read on **tape 1**, cross off a 0 on **tape 2**. If all 0s are crossed off before all the 1s are read, *reject*.
+   4. If all the 0s have now been crossed off, *accept*. If any 0s remain, *reject*.”