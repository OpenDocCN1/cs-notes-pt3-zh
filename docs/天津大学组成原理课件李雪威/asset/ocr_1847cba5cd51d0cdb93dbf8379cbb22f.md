# # Observations About Recursion

# ## Handled Without Special Consideration

+   - Stack frames mean that each function call has private storage
+     - Saved registers & local variables
+     - Saved return pointer

+   - Register saving conventions prevent one function call from corrupting another’s data
+     - Unless the C code explicitly does so (e.g., buffer overflow in Lecture 9)

+   - Stack discipline follows call / return pattern
+     - If P calls Q, then Q returns before P
+     - Last-In, First-Out

# ## Also works for mutual recursion

+   - P calls Q; Q calls P