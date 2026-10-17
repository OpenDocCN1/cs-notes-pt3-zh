# # Carry look ahead adder (CLA)

+   - Separation of
+     - add operation
+     - carry calculation
+   - Factorisation
+     - \( C_{i+1} = b_i c_i + a_i c_i + a_i b_i \)
+       \( = a_i b_i + a_i + b_i c_i \)
+     - Generate \( g_i = a_i b_i \)
+     - Propagate \( p_i = a_i + b_i \)