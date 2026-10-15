# Pipeline Summary

+   - Data Hazards
+     - Most handled by forwarding
+       - No performance penalty
+     - Load/use hazard requires one cycle stall
+   - Control Hazards
+     - Cancel instructions when detect mispredicted branch
+       - Two clock cycles wasted
+     - Stall fetch stage while `ret` passes through pipeline
+       - Three clock cycles wasted