# § 5.5: Program Correctness

+   - We want to be able to *prove* that a given program meets the intended specifications.
+     - This can often be done manually, or even by *automated program verification* tools.
+       - One example is PVS (People’s Verification System).
+   - A program is *correct* if it produces the correct output for every possible input.
+     - A program has *partial correctness* if it produces the correct output for every input for which the program eventually halts.