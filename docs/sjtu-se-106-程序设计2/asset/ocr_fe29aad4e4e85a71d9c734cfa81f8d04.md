# Counting Operations

+   - Another way to estimate the running time is to count how many operations are required to sort an array of size N.
+   - In the selection sort implementation, the section of code that is executed most frequently (and therefore contributes the most to the running time) is the body of the `findSmallest` method. The number of operations involved in each call to `findSmallest` changes as the algorithm proceeds:
+     - N values are considered on the first call to `findSmallest`.
+     - N − 1 values are considered on the second call.
+     - N − 2 values are considered on the third call, and so on.
+   - In mathematical notation, the number of values considered in `findSmallest` can be expressed as a summation, which can then be transformed into a simple formula:
+     1 + 2 + 3 + ⋯ + (N − 1) + N = ∑_{i=1}^{N} i = (N × (N + 1)) / 2