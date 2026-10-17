# # Signed number representation

First idea:

Positive and negative numbers

Take one bit (e.g. 31) as the **sign bit**

+   - Problem
+   - `0 0000000 = 0` — positive zero!
+   - `1 0000000 = 0` — negative zero!

Each comparison to 0 requires two steps

+   - 1's complement
+   - 2's complement