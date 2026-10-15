# Selection: algorithm

+   Procedure select(A, low, high, k)
+   1. p ← high − low + 1
+   2. if p < 44 then sort A and return (A[k])
+   3. Let q = ⌊p/5⌋. Divide A into q groups of 5 elements each. If 5 does not divide p, then discard the remaining elements.
+   4. Sort each of the q groups individually and extract its median. Let the set of the medians be M.
+   5. mm ← select(M, 1, q, ⌈q/2⌉)
+   6. Partition A[low..high] into three arrays:
+      A₁ = {a | a < mm}; A₂ = {a | a = mm}
+      A₃ = {a | a > mm}
+   7. case
+      |A₁| ≥ k: return select(A₁, 1, |A₁|, k)
+      |A₁| < k and |A₁| + |A₂| ≥ k: return mm
+      |A₁| + |A₂| < k: return select(A₃, 1, |A₃|, k − |A₁| − |A₂|)
+   8. end case