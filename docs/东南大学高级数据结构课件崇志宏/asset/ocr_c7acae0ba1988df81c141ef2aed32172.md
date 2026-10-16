# Height

+   - The running time of the search an insertion algorithms is affected by the height $h$ of the skip list
+   - We show that with high probability, a skip list with $n$ items has height $O(\log n)$
+   - We use the following additional probabilistic fact:
+     Fact 3: If each of $n$ events has probability $p$, the probability that at least one event occurs is at most $np$

+   - Consider a skip list with $n$ items
+     - By Fact 1, we insert an item in list $S_i$ with probability $1/2^i$
+     - By Fact 3, the probability that list $S_i$ has at least one item is at most $n/2^i$
+   - By picking $i = 3\log n$, we have that the probability that $S_{3\log n}$ has at least one item is at most
+     $n/2^{3\log n} = n/n^3 = 1/n^2$
+   - Thus a skip list with $n$ items has height at most $3\log n$ with probability at least $1 - 1/n^2$