# # Multiple Light Sources

+   - In case of multiple light sources, the terms for each light source are summed. So for **_m_** light sources the illumination equation is

\( I = I_a k_a + \sum_{1 \leq i \leq m} I_{pi}[k_d(\overline{N} \bullet \overline{L_i}) + k_s(\overline{R_i} \bullet \overline{V})^n] \)

+   - With summation it is possible that the value of _I_ might exceed the maximum displayable pixel value
+     - it could be avoided with proper selection of material
+     - the resulting value of _I_ could be clamped to the maximum value
+     - divide each pixel value by the peak value of _I_