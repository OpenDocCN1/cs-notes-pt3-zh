# # Analysis

Time = \( O(h) = O(\lg n) \), since INTERVAL-SEARCH does constant work at each level as it follows a simple path down the tree.

List _all_ overlapping intervals:

+   - Search, list, delete, repeat.
+   - Insert them all again at the end.

Time = \( O(k \lg n) \), where _k_ is the total number of overlapping intervals.

This is an **output-sensitive** bound.

Best algorithm to date: \( O(k + \lg n) \).