# # Other Aspects of FP Code

+   - **Lots of instructions**
+     - Different operations, different formats, ...
+   - **Floating-point comparisons**
+     - Instructions `ucomiss` and `ucomisd`
+     - Set condition codes CF, ZF, and PF
+   - **Using constant values**
+     - Set XMM0 register to 0 with instruction `xorpd %xmm0, %xmm0`
+     - Others loaded from memory