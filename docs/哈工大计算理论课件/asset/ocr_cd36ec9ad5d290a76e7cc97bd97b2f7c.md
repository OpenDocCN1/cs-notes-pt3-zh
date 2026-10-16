# Analyzing algorithm

+   M₁ = “On input string w:
+   1. Scan across the tape and reject if a 0 is found to the right of a 1.
+   2. Repeat if both 0s a
+   3. Scan across th and a single 1.
+   4. If 0s still remain a off, or if 1s still r crossed off, reject. remain on the tape

In stage 1, the machine scans across the tape to verify that the input is of the form 0*1*

Performing this scan uses k (k≤n) steps, and repositioning the head at the left-hand use k steps.

Totally use O(n)