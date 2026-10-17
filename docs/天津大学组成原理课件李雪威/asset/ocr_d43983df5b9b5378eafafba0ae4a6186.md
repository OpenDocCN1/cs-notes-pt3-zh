# # FP Multiplication

+   - \((-1)^{s1} M1\ 2^{E1} \times (-1)^{s2} M2\ 2^{E2}\)

+   - **Exact Result:** \((-1)^s M\ 2^E\)
+     - Sign \(s\): \(s1 \mathbin{\hat{~}} s2\)
+     - Significand \(M\): \(M1 \times M2\)
+     - Exponent \(E\): \(E1 + E2\)

+   - **Fixing**
+     - If \(M \ge 2\), shift \(M\) right, increment \(E\)
+     - If \(E\) out of range, overflow
+     - Round \(M\) to fit `frac` precision

+   - **Implementation**
+     - Biggest chore is multiplying significands

```
4 bit mantissa: 1.010*2² × 1.110*2³ = 10.0011*2⁵
                         = 1.00011*2⁶ = 1.001*2⁶
```