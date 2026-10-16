# The TQBF Problem

+   - Theorem:
+     - TQBF is PSPACE-complete
+   - Proof Idea:
+     - We give a straightforward algorithm that assigns values to the variables and recursively evaluates the truth of the formula for those values
+     - Then, we show every language A in PSPACE reduces to TQBF in polynomial time
+       - We begin with a polynomial space-bounded TM for A
+     - Then, we give a polynomial time reduction between them
+       - The φ will be true iff the machine accepts