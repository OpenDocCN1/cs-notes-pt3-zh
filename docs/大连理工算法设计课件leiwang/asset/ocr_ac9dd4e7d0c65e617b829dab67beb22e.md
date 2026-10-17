# What makes an algorithm randomized:

An algorithm is randomized if its behavior is determined in part by values produced by a random-number generator.

+   - **Random(a, b)** returns an integer *r*, where *a* ≤ *r* ≤ *b* and each of the *b* − *a* + 1 possible values of *r* is equally likely.
+   - In practice, Random is implemented by a **pseudorandom-number generator**, which is a deterministic method returning numbers that “look” random and pass statistical tests.