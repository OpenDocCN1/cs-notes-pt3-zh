# Multiplication

+   - Computing Exact Product of w-bit numbers x, y
+     - Either signed or unsigned
+   - Ranges
+     - Unsigned: 0 ≤ x * y ≤ (2^w - 1)^2 = 2^{2w} - 2^{w+1} + 1
+       - Up to 2w bits
+     - Two’s complement min: x * y ≥ -2^{w-1}*(2^{w-1}-1) = -2^{2w-2} + 2^{w-1}
+       - Up to 2w-1 bits
+     - Two’s complement max: x * y ≤ (-2^{w-1})^2 = 2^{2w-2}
+       - Up to 2w bits, but only for TMinw^2