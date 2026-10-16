# Examples of problems in NP

+   - Prove *SUBSET-SUM* is in **NP**.
+   - Proof I:
+   - Construct a verifier V.
+   - V = “ On input ⟨⟨s,k⟩,c⟩
+     1. Test whether c is a collection of numbers that sum to t.
+     2. Test whether S contains all the numbers in c.
+     3. If both pass, *accept*; otherwise, *reject*.”