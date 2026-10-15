# Answers to Floating Point Puzzles

+   - **Conversions**
+     - Casting between int, float, and double changes numeric values
+     - Double or float to int
+       - Truncates fractional part
+       - Like rounding toward zero
+       - Not defined when out of range
+         - *Generally saturates to TMin or TMax*
+     - int to double
+       - Exact conversion, as long as int has ≤ 53 bit word size
+     - int to float
+       - Will round according to rounding mode