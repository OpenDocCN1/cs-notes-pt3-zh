# # Worst-case of quicksort

+   - Input sorted or reverse sorted.
+   - Partition around min or max element.
+   - One side of partition always has no elements.

T(n) = T(0) + T(n-1) + Θ(n)
= Θ(1) + T(n-1) + Θ(n)
= T(n-1) + Θ(n)
= Θ(n²)   (arithmetic series)