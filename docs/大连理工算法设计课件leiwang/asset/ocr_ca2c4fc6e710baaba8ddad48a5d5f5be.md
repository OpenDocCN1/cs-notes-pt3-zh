# Brute-force LCS algorithm

Check every subsequence of x[1 .. m] to see if it is also a subsequence of y[1 .. n].



+   - Checking = O(n) time per subsequence.
+   - 2^m subsequences of x (each bit-vector of length m determines a distinct subsequence of x).

Worst-case running time = O(n2^m)
= exponential time.