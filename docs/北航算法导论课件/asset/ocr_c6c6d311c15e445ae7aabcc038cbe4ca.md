# 2.3.1 The divide-and-conquer approach

+   - **MERGE(A,p,q,r):** the key operation of the MERGE sort algorithm, the merging of two sorted sequences in the “combine” step.
+     - *A* is an array and *p, q,* and *r* are indices numbering elements of the array such that *p ≤ q < r*.
+     - The procedure assumes the subarrays *A[p .. q]* and *A[q+1 .. r]* are in sorted order. The procedure merges them to form a single sorted subarray that replaces the current subarray *A[p .. r]*.
+     - Working step:

The procedure takes time Θ(n), n=r-p+1