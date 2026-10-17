# # Multiplication

+   - Goal: Computing Product of \( w \)-bit numbers \( x \), \( y \)
+     - Either signed or unsigned

+   - But, exact results can be bigger than \( w \) bits
+     - Unsigned: up to \( 2w \) bits
+       - Result range: \( 0 \leq x * y \leq (2^w - 1)^2 = 2^{2w} - 2^{w+1} + 1 \)
+     - Two’s complement min (negative): Up to \( 2w-1 \) bits
+       - Result range: \( x * y \geq (-2^{w-1}) * (2^{w-1}-1) = -2^{2w-2} + 2^{w-1} \)
+     - Two’s complement max (positive): Up to \( 2w \) bits, but only for \( (TMin_w)^2 \)
+       - Result range: \( x * y \leq (-2^{w-1})^2 = 2^{2w-2} \)

+   - So, maintaining exact results...
+     - would need to keep expanding word size with each product computed
+     - is done in software, if needed
+       - e.g., by “arbitrary precision” arithmetic packages