# NL-Completeness

+   - Proof
+     - Instead, $A$’s machine $M_A$ computes individual symbols of $f(w)$ as requested by $B$’s machine $M_B$.
+     - In the simulation, $M_A$ keeps track of where $M_B$’s input head would be on $f(w)$
+     - Every time $M_B$ moves, $M_A$ restarts the computation of $f$ on $w$
+     - Doing so may require occasional recompilation of parts of $f(w)$ and so is inefficient in time complexity
+     - The advantage is that only a single symbol of $f(w)$ needs to be stored at any point
+     - It trade-off time for space