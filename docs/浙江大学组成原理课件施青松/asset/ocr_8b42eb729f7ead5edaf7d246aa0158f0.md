# Booth's Algorithm rule

# Analysis of two consecutive bits

| Current | last | Explanation | Example |
|---|---|---|---|
| 1 | 0 | Beginning | 000011110000 |
| 1 | 1 | middle of '1' | 000011110000 |
| 0 | 1 | End | 000011110000 |
| 0 | 0 | Middle of '0' | 000011110000 |

# Action

+   10 subtract multiplicand from left
+   11 no arithmetic operation
+   01 add multiplicand to left half
+   00 no arithmetic operation

+   Bit₋₁ = '0'

+   Arithmetic shift right:
+     - keeps the **leftmost bit constant**
+     - no change of sign bit !