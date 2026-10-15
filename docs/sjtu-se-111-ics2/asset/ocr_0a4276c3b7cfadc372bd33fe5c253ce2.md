# # Getting High Performance

+   - Good compiler and flags
+   - Don’t do anything stupid
+     - Watch out for hidden algorithmic inefficiencies
+     - Write compiler-friendly code
+       - Watch out for optimization blockers: procedure calls & memory references
+     - Look carefully at innermost loops
+   - Tune code for machine
+     - Exploit instruction-level parallelism
+     - Avoid unpredictable branches
+     - Make code cache friendly