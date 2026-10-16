# Working-Set Model

+   - Δ ≡ working-set window ≡ a fixed number of page references
+     Example: 10,000 instruction
+   - WSSᵢ (working set size of Process Pᵢ) = total number of pages referenced in the most recent Δ (varies in time)
+     - if Δ too small will not encompass entire locality.
+     - if Δ too large will encompass several localities.
+     - if Δ = ∞ ⇒ will encompass entire program.
+   - D = Σ WSSᵢ ≡ total demand frames
+   - if D > m ⇒ Thrashing
+   - Policy if D > m, then suspend one of the processes.