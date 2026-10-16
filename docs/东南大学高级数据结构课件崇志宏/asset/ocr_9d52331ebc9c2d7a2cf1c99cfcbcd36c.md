# Search and Update Times

+   - The search time in a skip list is proportional to
+     - the number of drop-down steps, plus
+     - the number of scan-forward steps
+   - The drop-down steps are bounded by the height of the skip list and thus are $O(\log n)$ with high probability
+   - To analyze the scan-forward steps, we use yet another probabilistic fact:
+     Fact 4: The expected number of coin tosses required in order to get tails is 2

+   - When we scan forward in a list, the destination key does not belong to a higher list
+     - A scan-forward step is associated with a former coin toss that gave tails
+   - By Fact 4, in each list the expected number of scan-forward steps is 2
+   - Thus, the expected number of scan-forward steps is $O(\log n)$
+   - We conclude that a search in a skip list takes $O(\log n)$ expected time
+   - The analysis of insertion and deletion gives similar results