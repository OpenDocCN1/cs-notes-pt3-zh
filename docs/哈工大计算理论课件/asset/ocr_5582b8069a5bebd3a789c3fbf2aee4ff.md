# Class NP

Proof:

+   Assume that V is polynomial time verifier for A and V is a TM that runs in time n^k and construct N as follows:

+   N = “On input w of length n:
+   1. Nondeterministically select string c of length at most n^k.
+   2. Run V on input <w,c>.
+   3. If V accepts, accept; otherwise, reject.”