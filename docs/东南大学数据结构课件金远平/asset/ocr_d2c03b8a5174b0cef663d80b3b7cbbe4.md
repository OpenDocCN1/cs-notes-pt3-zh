# Analysis of HeapSort:

+   - suppose 2^{k-1} ≤ n < 2^{k}, the tree has k levels.
+   - the number of nodes on level i ≤ 2^{i-1}.
+   - in the first loop, Adjust is called once for each node that has a child, hence the time is no more than

∑_{1≤i≤k-1} 2^{i-1}(k−i) =

∑_{1≤i≤k-1} 2^{k-i-1} i ≤ n ∑_{1≤i≤k-1} i/2^{i} < 2n = O(n)

![](bbox=[0.78, 0.42, 0.98, 0.88])