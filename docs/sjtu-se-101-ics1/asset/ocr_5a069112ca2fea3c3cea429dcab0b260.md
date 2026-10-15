# Observations

+   - The loop will access the elements of array B
+     - as B[0][k], B[1][k], ..., B[15][k] in sequence
+   - These elements occupy positions in memory
+     - starting with the address of array B[0][i]
+     - and space 64 bytes apart.
+   - Use a pointer variable Bptr
+     - to access these locations.
+   - Use a simple counter
+     - to keep track of the number of iterations required