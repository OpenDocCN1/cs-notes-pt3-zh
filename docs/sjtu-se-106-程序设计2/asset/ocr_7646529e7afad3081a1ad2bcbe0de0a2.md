# # How Many Levels Are There?

+   - The number of levels in the merge sort decomposition is equal to the number of times you can divide the original vector in half until there is only one element remaining. In other words, what you need to find is the value of $k$ that satisfies the following equation:
+   
+     $$1 = N / 2 / 2 / 2 / 2 / \cdots / 2$$
+   
+     *(2 is divided $k$ times.)*

+   - You can simplify this formula using basic mathematics:
+   
+     $$1 = N / 2^k$$
+     $$2^k = N$$
+     $$k = \log_2 N$$

+   - The complexity of merge sort is therefore $O(N \log N)$.