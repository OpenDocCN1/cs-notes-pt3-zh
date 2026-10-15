# Setting Conditional Codes

+   - Explicit Setting by Test instruction
+     - `testl Src2,Src1`
+     - Sets condition codes based on value of *Src1* & *Src2*
+       - Useful to have one of the operands be a mask
+     - `testl b,a` like computing `a&b` without setting destination
+     - ZF set when `a&b == 0`
+     - SF set when `a&b < 0`