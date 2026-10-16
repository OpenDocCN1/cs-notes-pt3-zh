# Recursion theorem

+   - Proof:
+   - Let F be the following Turing machine:
+   - F = “On input w:
+     1. Obtain, via the recursion theorem, own description <F>.
+     2. Compute t (<F>) to obtain the description of a TM G.
+     3. Simulate G on w.”
+   - So <F> and t (<F>) = <G> describe equivalent Turing machines because F simulates G.