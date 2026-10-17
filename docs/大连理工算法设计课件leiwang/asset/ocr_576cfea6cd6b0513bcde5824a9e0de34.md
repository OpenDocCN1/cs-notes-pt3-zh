# BUILD-MAX-HEAP(A)

+   1 heap-size[A] ← length[A]
+   2 for i ← ⌊length[A]/2⌋ downto 1
+   3 do MAX-HEAPIFY(A, i)